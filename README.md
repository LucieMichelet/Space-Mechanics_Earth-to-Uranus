# Space-Mechanics
# Project : Eart to Uranus

#### Students : Hugo LANCERY - Lucie MICHELET - ELSS


```python
import numpy as np
```

### Library


```python
def param(mue,V,R,mod):
    """
    Parameters
    ----------
    mue : reduced gravitational constant of the planet
    V : Velocity of the spacecraft
    R : radius
    mod : elliptic or hyperbola 

    Returns
    -------
    a : apoapsis 
    e : eccentricity 
    w : total energy [km.s-2]
    t : orital period [s]

    """
    if mod == 'e' :
        a = -mue/(2*(V**2/2-mue/R))
        e = -R/a+1
        w = -mue/(2*a)
    if mod == 'h' :
        a = mue/(2*(V**2/2-mue/R))
        e = 1+R/a
        w = mue/(2*a)
    t = 2*np.pi*np.sqrt(a**3/mue)
    return a,e,w,t

def Vl(mue,d):
    """
    Parameters
    ----------
    mue : int - gravitaional reduced param.
    R : int - distance

    Returns
    -------
    float - The velocity for liberation
    """
    return np.sqrt(2*mue/d)


def V(mue,R):
    return np.sqrt(mue/R)


def E_h(R,a,e):
    return np.log((Ro/a+1)*(e**-1)+np.sqrt(((R/a+1)*e**-1)**2-1))

def t_tp_h(E,a,e,mue,tp=0):
    #/!\ E en radian pour les calculs
    return (np.sqrt(a**3/mue))*(e*np.sinh(E)-E)+tp


def E_e(R,a,e):
    return np.arccos((R/a-1)/(-e))

def t_tp_e(E,a,e,mue,tp=0):
    return (np.sqrt(a**3/mue))*(E - e*np.sin(E))+tp


def Vrot(R,T):
    return 2*np.pi*R/T


def Vs(V1,V2,angle):
    return np.sqrt(V1**2+V2**2+2*V1*V2*np.cos(angle))


def deltaV(V1,V2):
    if V2 > V1 :
        print("Thanks to Jupiter influence, we accelerated !")
        deltaV = V2-V1
        
    if V1 > V2 :
        print("Thanks to Jupiter influence, we decelerated !")
        deltaV = V1-V2
    
    if V1 == V2 :
        print("Jupiter influence didn't affect the velocity of the spacecraft.")
        deltaV = 0
        
    return deltaV

```

### Importation of the data


```python
#Constante gravitationelle
G = 6.67428*10**(-11)

# Masse [kg]
mT = 5.9737*10**(24)
mU = 8.681*10**(25)

# gravitational reduced param [km**3/s**2]
mueE = G*mT/(1000**3) 
mueU = G*mU/(1000**3)
mueS = 13.2*10**10
mueJ = 126.5*10**6

# distance au soleil
sJ = 750*10**6
sU = 2.9*10**9
sT = 150*10**6

# Rayons en [km]
rT = 6878
rJ = 71400
rU = 25362 
h = 200
omgp = h +rT

```

### Initial State

We calculate the velocity of satelization and liberation of our satellite and its parameters


```python
vsat = (mueE/omgp)**0.5
vlib = Vl(mueE,omgp)

#param initial state
a = -mueE/(2*(vsat**2/2-mueE/omgp))
e = 0   # because LEO
t = 2*np.pi*np.sqrt(a**3/mueE)

print("Satelization velocity : ",vsat,"\nLiberation Velocity : ",vlib)
```

    Satelization velocity :  7.505310019652698 
    Liberation Velocity :  10.614111219607524
    

### First Tranfert Orbit - leaving Earth inlfuence

Then we add velocity to exit the earth influence


```python
#acceleration to have an hyperbola
dv0 = 6.66
v0 = vsat + dv0
a0,e0,w0,T0 = param(mueE,v0,omgp,'h')

phi0 = np.arccos(1/e0)*180/np.pi

#%% Calculation of time for entering jupiter area

Ro = 900000
tp = 0

E0 = E_h(Ro,a0,e0)
E0deg = E0*180/np.pi

t0 = t_tp_h(E0,a0,e0,mueE,tp) 
print(t0/60/60,'hours')

n = (mueE/(a0**3))**0.5 
```

    26.105181118306 hours
    

Now we want to know what is the velocity needed to enter jupiter influence


```python
#velocity at limite of the earth influence sphere
VinfE = V(mueE,a0)

ua = 150*10**6
TrotE = 365.25*86400


#velocity rot earth
VrotE = Vrot(ua,TrotE)

angle_V_deg = 19.53  
angle_V = 19.53*np.pi/180

#injection velocity 
Vso = Vs(VinfE,VrotE,angle_V)
Vl1 = Vl(mueS,ua)
# Vl1 > Vso so we have an ellipse

print("Velocity needed : ",Vl1)
print("Velocity we have : ",Vso)
```

    Velocity needed :  41.95235392680606
    Velocity we have :  38.83309985869477
    

We determine the date of rendez-vous with Jupiter


```python
#The parameter of the trajectory once the injection is done
a1,e1,w1,T1 = param(mueS,Vso,ua,'e')
```


```python
E1 = E_e(sJ,a1,e1)

t1 = t_tp_e(E1,a1,e1,mueS)
print("Time of transfer : ",t1/60/60/24/365,'year')
```

    Time of transfer :  1.728999282487167 year
    


```python
# Velocity jupiter to the sun
Vj = V(mueS,sJ)
print("Velocity of Jupiter : ",Vj)
```

    Velocity of Jupiter :  13.2664991614216
    


```python
# velocity of the spacecraft, related to Sun, at the level of Jupiter orbit and the angle of crossing orbit directions
   
Vs1 = np.sqrt(2*(-mueS/(2*a1)+mueS/sJ))   #[km/s]
phi1 = np.arccos(Vso*ua/(Vs1*sJ))
phi1deg = phi1*180/np.pi

print(Vs1)
```

    10.000482220141187
    


```python
# velocity of the spacecraft, related to Jupiter, at the entry point and the angle

Vinf1 = np.sqrt(Vs1**2+Vj**2-2*Vs1*Vj*np.cos(phi1))
alpha1 = np.arcsin(np.sin(phi1)/Vinf1*Vs1)
alpha1deg = alpha1*180/np.pi

print(Vinf1)
```

    8.36289004776757
    

### Arrival in the Jupiter neighborhood

We determine the following parameters of the flyby trajectory at 50000 km altitude


```python
h1 = 0.18*rJ
Rj = rJ+h1        

aj = mueJ/(Vinf1**2)
ej = 1+Rj/aj
phij = np.arccos(1/ej)
phijdeg = phij*180/np.pi

alphajdeg = 180-2*phijdeg-alpha1deg
alphaj = alphajdeg*np.pi/180
```

Now we want to determine the exit conditions of the Jovian sphere


```python
# velocity of the spacecraft, related to Sun, at the Jovian exit point and its angle

Vs2 = Vs(Vinf1,Vj,alphaj)
phi2 = np.arccos(1/(1+Rj/(mueJ/(Vs2**2))))

dV = deltaV(Vs1,Vs2)

print("\nVelocity at the Jovian exit point : ",Vs2,"\nPhi angle : ",phi2*180/np.pi)
```

    Thanks to Jupiter influence, we accelerated !
    
    Velocity at the Jovian exit point :  14.820537467937143 
    Phi angle :  29.263737168029998
    

### Second Transfert Orbit : leaving Jupiter influence
By hypothesis, the heliocentric orbit at the exit point of Jupiter influence sphere are:
r = sJ 
v = Vs2
phi = phi2 = 32.65°
We determine the parameters of the new orbit


```python
Vl2 = Vl(mueS,sJ)
print("Velocity needed to leave Jupiter influence :",Vl2)

#Vs2<Vl2 so ellipse
```

    Velocity needed to leave Jupiter influence : 18.76166303929372
    


```python
#We add velocity to have an hyperbola
dv3 =  3.98
Vs3 = Vs2 + dv3

#Vs3>Vl2
a3,e3,w3,T3 = param(mueS,Vs3,sJ,'h')

print(e3)
```

    1.0082966425187976
    

We calculate the time of rendez vous with Uranus


```python
E3 = E_h(sU,a3,e3)
t3 = t_tp_h(E3,a3,e3,mueS)

print(t3/60/60/24/365,"years")
```

    6.531318218837246 years
    

### Total time


```python
print((t0+t1+t3)/60/60/24/365)
```

    8.263297544831067
    

### Arrival on Uranus


```python
# Velocity Uranus
Vu = V(mueS,sU)
print(Vu)
```

    6.7466466766320545
    


```python
# velocity of the spacecraft, related to Sun, at the level of Uranus orbit and the angle of crossing orbit directions
Vs4 = np.sqrt(2*(-mueS/(2*a3)+mueS/sU))   #[km/s]
phi3 = np.arccos(Vs3*sJ/(Vs4*sU))
phi3deg = phi3*180/np.pi

print(Vs4)
```

    9.4643686358527
    


```python
# velocity of the spacecraft, related to Uranus, at the entry point and the angle
Vinf4 = Vs(Vs4,Vu,phi3)
print(Vinf4)
```

    14.16681733779178
    


```python
#Defining the orbit altitude
h3 = 12000
Ru = rU+h3  
```


```python
#Satelization velocity of Uranus
VsatU = np.sqrt(mueU/Ru)
print("Vsat Uranus :",VsatU)
```

    Vsat Uranus : 12.452943887539027
    


```python
#Liberation velocity of Uranus
VlU = Vl(mueU,Ru)
print(VlU)
```

    17.611122137228826
    


```python
#Vinf4 < VlU = ellipse
aU,eU,wU,Tu = param(mueU,Vinf4,Ru,'e')

print(eU)#ellipse
```

    0.29419740954318563
    

The velocity of the stalletite is between the satellization velocity and the liberation velocity. We are in orbit around Uranus. We don't need to add velocity to have an orbit around Uranus !

### Calculation of the cost 


```python
dvTot = dv0+dv3 
print(dvTot)
```

    10.64
    

We have a final coast of 10.64 km/s


```python
m = 12
ISP = 230
#solid ergol

Ec = 0.5*m*dvTot**2
print(Ec,"N")

conso = Ec/(ISP)
print(conso,"kg/s")

#print("total conso : ")
```

    679.2576 N
    2.9532939130434785 kg/s
    


```python

```
