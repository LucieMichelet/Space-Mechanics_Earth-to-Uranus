# Space-Mechanics
\documentclass[11pt]{article}

    \usepackage[breakable]{tcolorbox}
    \usepackage{parskip} % Stop auto-indenting (to mimic markdown behaviour)
    
    \usepackage{iftex}
    \ifPDFTeX
    	\usepackage[T1]{fontenc}
    	\usepackage{mathpazo}
    \else
    	\usepackage{fontspec}
    \fi

    % Basic figure setup, for now with no caption control since it's done
    % automatically by Pandoc (which extracts ![](path) syntax from Markdown).
    \usepackage{graphicx}
    % Maintain compatibility with old templates. Remove in nbconvert 6.0
    \let\Oldincludegraphics\includegraphics
    % Ensure that by default, figures have no caption (until we provide a
    % proper Figure object with a Caption API and a way to capture that
    % in the conversion process - todo).
    \usepackage{caption}
    \DeclareCaptionFormat{nocaption}{}
    \captionsetup{format=nocaption,aboveskip=0pt,belowskip=0pt}

    \usepackage{float}
    \floatplacement{figure}{H} % forces figures to be placed at the correct location
    \usepackage{xcolor} % Allow colors to be defined
    \usepackage{enumerate} % Needed for markdown enumerations to work
    \usepackage{geometry} % Used to adjust the document margins
    \usepackage{amsmath} % Equations
    \usepackage{amssymb} % Equations
    \usepackage{textcomp} % defines textquotesingle
    % Hack from http://tex.stackexchange.com/a/47451/13684:
    \AtBeginDocument{%
        \def\PYZsq{\textquotesingle}% Upright quotes in Pygmentized code
    }
    \usepackage{upquote} % Upright quotes for verbatim code
    \usepackage{eurosym} % defines \euro
    \usepackage[mathletters]{ucs} % Extended unicode (utf-8) support
    \usepackage{fancyvrb} % verbatim replacement that allows latex
    \usepackage{grffile} % extends the file name processing of package graphics 
                         % to support a larger range
    \makeatletter % fix for old versions of grffile with XeLaTeX
    \@ifpackagelater{grffile}{2019/11/01}
    {
      % Do nothing on new versions
    }
    {
      \def\Gread@@xetex#1{%
        \IfFileExists{"\Gin@base".bb}%
        {\Gread@eps{\Gin@base.bb}}%
        {\Gread@@xetex@aux#1}%
      }
    }
    \makeatother
    \usepackage[Export]{adjustbox} % Used to constrain images to a maximum size
    \adjustboxset{max size={0.9\linewidth}{0.9\paperheight}}

    % The hyperref package gives us a pdf with properly built
    % internal navigation ('pdf bookmarks' for the table of contents,
    % internal cross-reference links, web links for URLs, etc.)
    \usepackage{hyperref}
    % The default LaTeX title has an obnoxious amount of whitespace. By default,
    % titling removes some of it. It also provides customization options.
    \usepackage{titling}
    \usepackage{longtable} % longtable support required by pandoc >1.10
    \usepackage{booktabs}  % table support for pandoc > 1.12.2
    \usepackage[inline]{enumitem} % IRkernel/repr support (it uses the enumerate* environment)
    \usepackage[normalem]{ulem} % ulem is needed to support strikethroughs (\sout)
                                % normalem makes italics be italics, not underlines
    \usepackage{mathrsfs}
    

    
    % Colors for the hyperref package
    \definecolor{urlcolor}{rgb}{0,.145,.698}
    \definecolor{linkcolor}{rgb}{.71,0.21,0.01}
    \definecolor{citecolor}{rgb}{.12,.54,.11}

    % ANSI colors
    \definecolor{ansi-black}{HTML}{3E424D}
    \definecolor{ansi-black-intense}{HTML}{282C36}
    \definecolor{ansi-red}{HTML}{E75C58}
    \definecolor{ansi-red-intense}{HTML}{B22B31}
    \definecolor{ansi-green}{HTML}{00A250}
    \definecolor{ansi-green-intense}{HTML}{007427}
    \definecolor{ansi-yellow}{HTML}{DDB62B}
    \definecolor{ansi-yellow-intense}{HTML}{B27D12}
    \definecolor{ansi-blue}{HTML}{208FFB}
    \definecolor{ansi-blue-intense}{HTML}{0065CA}
    \definecolor{ansi-magenta}{HTML}{D160C4}
    \definecolor{ansi-magenta-intense}{HTML}{A03196}
    \definecolor{ansi-cyan}{HTML}{60C6C8}
    \definecolor{ansi-cyan-intense}{HTML}{258F8F}
    \definecolor{ansi-white}{HTML}{C5C1B4}
    \definecolor{ansi-white-intense}{HTML}{A1A6B2}
    \definecolor{ansi-default-inverse-fg}{HTML}{FFFFFF}
    \definecolor{ansi-default-inverse-bg}{HTML}{000000}

    % common color for the border for error outputs.
    \definecolor{outerrorbackground}{HTML}{FFDFDF}

    % commands and environments needed by pandoc snippets
    % extracted from the output of `pandoc -s`
    \providecommand{\tightlist}{%
      \setlength{\itemsep}{0pt}\setlength{\parskip}{0pt}}
    \DefineVerbatimEnvironment{Highlighting}{Verbatim}{commandchars=\\\{\}}
    % Add ',fontsize=\small' for more characters per line
    \newenvironment{Shaded}{}{}
    \newcommand{\KeywordTok}[1]{\textcolor[rgb]{0.00,0.44,0.13}{\textbf{{#1}}}}
    \newcommand{\DataTypeTok}[1]{\textcolor[rgb]{0.56,0.13,0.00}{{#1}}}
    \newcommand{\DecValTok}[1]{\textcolor[rgb]{0.25,0.63,0.44}{{#1}}}
    \newcommand{\BaseNTok}[1]{\textcolor[rgb]{0.25,0.63,0.44}{{#1}}}
    \newcommand{\FloatTok}[1]{\textcolor[rgb]{0.25,0.63,0.44}{{#1}}}
    \newcommand{\CharTok}[1]{\textcolor[rgb]{0.25,0.44,0.63}{{#1}}}
    \newcommand{\StringTok}[1]{\textcolor[rgb]{0.25,0.44,0.63}{{#1}}}
    \newcommand{\CommentTok}[1]{\textcolor[rgb]{0.38,0.63,0.69}{\textit{{#1}}}}
    \newcommand{\OtherTok}[1]{\textcolor[rgb]{0.00,0.44,0.13}{{#1}}}
    \newcommand{\AlertTok}[1]{\textcolor[rgb]{1.00,0.00,0.00}{\textbf{{#1}}}}
    \newcommand{\FunctionTok}[1]{\textcolor[rgb]{0.02,0.16,0.49}{{#1}}}
    \newcommand{\RegionMarkerTok}[1]{{#1}}
    \newcommand{\ErrorTok}[1]{\textcolor[rgb]{1.00,0.00,0.00}{\textbf{{#1}}}}
    \newcommand{\NormalTok}[1]{{#1}}
    
    % Additional commands for more recent versions of Pandoc
    \newcommand{\ConstantTok}[1]{\textcolor[rgb]{0.53,0.00,0.00}{{#1}}}
    \newcommand{\SpecialCharTok}[1]{\textcolor[rgb]{0.25,0.44,0.63}{{#1}}}
    \newcommand{\VerbatimStringTok}[1]{\textcolor[rgb]{0.25,0.44,0.63}{{#1}}}
    \newcommand{\SpecialStringTok}[1]{\textcolor[rgb]{0.73,0.40,0.53}{{#1}}}
    \newcommand{\ImportTok}[1]{{#1}}
    \newcommand{\DocumentationTok}[1]{\textcolor[rgb]{0.73,0.13,0.13}{\textit{{#1}}}}
    \newcommand{\AnnotationTok}[1]{\textcolor[rgb]{0.38,0.63,0.69}{\textbf{\textit{{#1}}}}}
    \newcommand{\CommentVarTok}[1]{\textcolor[rgb]{0.38,0.63,0.69}{\textbf{\textit{{#1}}}}}
    \newcommand{\VariableTok}[1]{\textcolor[rgb]{0.10,0.09,0.49}{{#1}}}
    \newcommand{\ControlFlowTok}[1]{\textcolor[rgb]{0.00,0.44,0.13}{\textbf{{#1}}}}
    \newcommand{\OperatorTok}[1]{\textcolor[rgb]{0.40,0.40,0.40}{{#1}}}
    \newcommand{\BuiltInTok}[1]{{#1}}
    \newcommand{\ExtensionTok}[1]{{#1}}
    \newcommand{\PreprocessorTok}[1]{\textcolor[rgb]{0.74,0.48,0.00}{{#1}}}
    \newcommand{\AttributeTok}[1]{\textcolor[rgb]{0.49,0.56,0.16}{{#1}}}
    \newcommand{\InformationTok}[1]{\textcolor[rgb]{0.38,0.63,0.69}{\textbf{\textit{{#1}}}}}
    \newcommand{\WarningTok}[1]{\textcolor[rgb]{0.38,0.63,0.69}{\textbf{\textit{{#1}}}}}
    
    
    % Define a nice break command that doesn't care if a line doesn't already
    % exist.
    \def\br{\hspace*{\fill} \\* }
    % Math Jax compatibility definitions
    \def\gt{>}
    \def\lt{<}
    \let\Oldtex\TeX
    \let\Oldlatex\LaTeX
    \renewcommand{\TeX}{\textrm{\Oldtex}}
    \renewcommand{\LaTeX}{\textrm{\Oldlatex}}
    % Document parameters
    % Document title
    \title{SpaceMechanics\_Projet}
    
    
    
    
    
% Pygments definitions
\makeatletter
\def\PY@reset{\let\PY@it=\relax \let\PY@bf=\relax%
    \let\PY@ul=\relax \let\PY@tc=\relax%
    \let\PY@bc=\relax \let\PY@ff=\relax}
\def\PY@tok#1{\csname PY@tok@#1\endcsname}
\def\PY@toks#1+{\ifx\relax#1\empty\else%
    \PY@tok{#1}\expandafter\PY@toks\fi}
\def\PY@do#1{\PY@bc{\PY@tc{\PY@ul{%
    \PY@it{\PY@bf{\PY@ff{#1}}}}}}}
\def\PY#1#2{\PY@reset\PY@toks#1+\relax+\PY@do{#2}}

\@namedef{PY@tok@w}{\def\PY@tc##1{\textcolor[rgb]{0.73,0.73,0.73}{##1}}}
\@namedef{PY@tok@c}{\let\PY@it=\textit\def\PY@tc##1{\textcolor[rgb]{0.25,0.50,0.50}{##1}}}
\@namedef{PY@tok@cp}{\def\PY@tc##1{\textcolor[rgb]{0.74,0.48,0.00}{##1}}}
\@namedef{PY@tok@k}{\let\PY@bf=\textbf\def\PY@tc##1{\textcolor[rgb]{0.00,0.50,0.00}{##1}}}
\@namedef{PY@tok@kp}{\def\PY@tc##1{\textcolor[rgb]{0.00,0.50,0.00}{##1}}}
\@namedef{PY@tok@kt}{\def\PY@tc##1{\textcolor[rgb]{0.69,0.00,0.25}{##1}}}
\@namedef{PY@tok@o}{\def\PY@tc##1{\textcolor[rgb]{0.40,0.40,0.40}{##1}}}
\@namedef{PY@tok@ow}{\let\PY@bf=\textbf\def\PY@tc##1{\textcolor[rgb]{0.67,0.13,1.00}{##1}}}
\@namedef{PY@tok@nb}{\def\PY@tc##1{\textcolor[rgb]{0.00,0.50,0.00}{##1}}}
\@namedef{PY@tok@nf}{\def\PY@tc##1{\textcolor[rgb]{0.00,0.00,1.00}{##1}}}
\@namedef{PY@tok@nc}{\let\PY@bf=\textbf\def\PY@tc##1{\textcolor[rgb]{0.00,0.00,1.00}{##1}}}
\@namedef{PY@tok@nn}{\let\PY@bf=\textbf\def\PY@tc##1{\textcolor[rgb]{0.00,0.00,1.00}{##1}}}
\@namedef{PY@tok@ne}{\let\PY@bf=\textbf\def\PY@tc##1{\textcolor[rgb]{0.82,0.25,0.23}{##1}}}
\@namedef{PY@tok@nv}{\def\PY@tc##1{\textcolor[rgb]{0.10,0.09,0.49}{##1}}}
\@namedef{PY@tok@no}{\def\PY@tc##1{\textcolor[rgb]{0.53,0.00,0.00}{##1}}}
\@namedef{PY@tok@nl}{\def\PY@tc##1{\textcolor[rgb]{0.63,0.63,0.00}{##1}}}
\@namedef{PY@tok@ni}{\let\PY@bf=\textbf\def\PY@tc##1{\textcolor[rgb]{0.60,0.60,0.60}{##1}}}
\@namedef{PY@tok@na}{\def\PY@tc##1{\textcolor[rgb]{0.49,0.56,0.16}{##1}}}
\@namedef{PY@tok@nt}{\let\PY@bf=\textbf\def\PY@tc##1{\textcolor[rgb]{0.00,0.50,0.00}{##1}}}
\@namedef{PY@tok@nd}{\def\PY@tc##1{\textcolor[rgb]{0.67,0.13,1.00}{##1}}}
\@namedef{PY@tok@s}{\def\PY@tc##1{\textcolor[rgb]{0.73,0.13,0.13}{##1}}}
\@namedef{PY@tok@sd}{\let\PY@it=\textit\def\PY@tc##1{\textcolor[rgb]{0.73,0.13,0.13}{##1}}}
\@namedef{PY@tok@si}{\let\PY@bf=\textbf\def\PY@tc##1{\textcolor[rgb]{0.73,0.40,0.53}{##1}}}
\@namedef{PY@tok@se}{\let\PY@bf=\textbf\def\PY@tc##1{\textcolor[rgb]{0.73,0.40,0.13}{##1}}}
\@namedef{PY@tok@sr}{\def\PY@tc##1{\textcolor[rgb]{0.73,0.40,0.53}{##1}}}
\@namedef{PY@tok@ss}{\def\PY@tc##1{\textcolor[rgb]{0.10,0.09,0.49}{##1}}}
\@namedef{PY@tok@sx}{\def\PY@tc##1{\textcolor[rgb]{0.00,0.50,0.00}{##1}}}
\@namedef{PY@tok@m}{\def\PY@tc##1{\textcolor[rgb]{0.40,0.40,0.40}{##1}}}
\@namedef{PY@tok@gh}{\let\PY@bf=\textbf\def\PY@tc##1{\textcolor[rgb]{0.00,0.00,0.50}{##1}}}
\@namedef{PY@tok@gu}{\let\PY@bf=\textbf\def\PY@tc##1{\textcolor[rgb]{0.50,0.00,0.50}{##1}}}
\@namedef{PY@tok@gd}{\def\PY@tc##1{\textcolor[rgb]{0.63,0.00,0.00}{##1}}}
\@namedef{PY@tok@gi}{\def\PY@tc##1{\textcolor[rgb]{0.00,0.63,0.00}{##1}}}
\@namedef{PY@tok@gr}{\def\PY@tc##1{\textcolor[rgb]{1.00,0.00,0.00}{##1}}}
\@namedef{PY@tok@ge}{\let\PY@it=\textit}
\@namedef{PY@tok@gs}{\let\PY@bf=\textbf}
\@namedef{PY@tok@gp}{\let\PY@bf=\textbf\def\PY@tc##1{\textcolor[rgb]{0.00,0.00,0.50}{##1}}}
\@namedef{PY@tok@go}{\def\PY@tc##1{\textcolor[rgb]{0.53,0.53,0.53}{##1}}}
\@namedef{PY@tok@gt}{\def\PY@tc##1{\textcolor[rgb]{0.00,0.27,0.87}{##1}}}
\@namedef{PY@tok@err}{\def\PY@bc##1{{\setlength{\fboxsep}{\string -\fboxrule}\fcolorbox[rgb]{1.00,0.00,0.00}{1,1,1}{\strut ##1}}}}
\@namedef{PY@tok@kc}{\let\PY@bf=\textbf\def\PY@tc##1{\textcolor[rgb]{0.00,0.50,0.00}{##1}}}
\@namedef{PY@tok@kd}{\let\PY@bf=\textbf\def\PY@tc##1{\textcolor[rgb]{0.00,0.50,0.00}{##1}}}
\@namedef{PY@tok@kn}{\let\PY@bf=\textbf\def\PY@tc##1{\textcolor[rgb]{0.00,0.50,0.00}{##1}}}
\@namedef{PY@tok@kr}{\let\PY@bf=\textbf\def\PY@tc##1{\textcolor[rgb]{0.00,0.50,0.00}{##1}}}
\@namedef{PY@tok@bp}{\def\PY@tc##1{\textcolor[rgb]{0.00,0.50,0.00}{##1}}}
\@namedef{PY@tok@fm}{\def\PY@tc##1{\textcolor[rgb]{0.00,0.00,1.00}{##1}}}
\@namedef{PY@tok@vc}{\def\PY@tc##1{\textcolor[rgb]{0.10,0.09,0.49}{##1}}}
\@namedef{PY@tok@vg}{\def\PY@tc##1{\textcolor[rgb]{0.10,0.09,0.49}{##1}}}
\@namedef{PY@tok@vi}{\def\PY@tc##1{\textcolor[rgb]{0.10,0.09,0.49}{##1}}}
\@namedef{PY@tok@vm}{\def\PY@tc##1{\textcolor[rgb]{0.10,0.09,0.49}{##1}}}
\@namedef{PY@tok@sa}{\def\PY@tc##1{\textcolor[rgb]{0.73,0.13,0.13}{##1}}}
\@namedef{PY@tok@sb}{\def\PY@tc##1{\textcolor[rgb]{0.73,0.13,0.13}{##1}}}
\@namedef{PY@tok@sc}{\def\PY@tc##1{\textcolor[rgb]{0.73,0.13,0.13}{##1}}}
\@namedef{PY@tok@dl}{\def\PY@tc##1{\textcolor[rgb]{0.73,0.13,0.13}{##1}}}
\@namedef{PY@tok@s2}{\def\PY@tc##1{\textcolor[rgb]{0.73,0.13,0.13}{##1}}}
\@namedef{PY@tok@sh}{\def\PY@tc##1{\textcolor[rgb]{0.73,0.13,0.13}{##1}}}
\@namedef{PY@tok@s1}{\def\PY@tc##1{\textcolor[rgb]{0.73,0.13,0.13}{##1}}}
\@namedef{PY@tok@mb}{\def\PY@tc##1{\textcolor[rgb]{0.40,0.40,0.40}{##1}}}
\@namedef{PY@tok@mf}{\def\PY@tc##1{\textcolor[rgb]{0.40,0.40,0.40}{##1}}}
\@namedef{PY@tok@mh}{\def\PY@tc##1{\textcolor[rgb]{0.40,0.40,0.40}{##1}}}
\@namedef{PY@tok@mi}{\def\PY@tc##1{\textcolor[rgb]{0.40,0.40,0.40}{##1}}}
\@namedef{PY@tok@il}{\def\PY@tc##1{\textcolor[rgb]{0.40,0.40,0.40}{##1}}}
\@namedef{PY@tok@mo}{\def\PY@tc##1{\textcolor[rgb]{0.40,0.40,0.40}{##1}}}
\@namedef{PY@tok@ch}{\let\PY@it=\textit\def\PY@tc##1{\textcolor[rgb]{0.25,0.50,0.50}{##1}}}
\@namedef{PY@tok@cm}{\let\PY@it=\textit\def\PY@tc##1{\textcolor[rgb]{0.25,0.50,0.50}{##1}}}
\@namedef{PY@tok@cpf}{\let\PY@it=\textit\def\PY@tc##1{\textcolor[rgb]{0.25,0.50,0.50}{##1}}}
\@namedef{PY@tok@c1}{\let\PY@it=\textit\def\PY@tc##1{\textcolor[rgb]{0.25,0.50,0.50}{##1}}}
\@namedef{PY@tok@cs}{\let\PY@it=\textit\def\PY@tc##1{\textcolor[rgb]{0.25,0.50,0.50}{##1}}}

\def\PYZbs{\char`\\}
\def\PYZus{\char`\_}
\def\PYZob{\char`\{}
\def\PYZcb{\char`\}}
\def\PYZca{\char`\^}
\def\PYZam{\char`\&}
\def\PYZlt{\char`\<}
\def\PYZgt{\char`\>}
\def\PYZsh{\char`\#}
\def\PYZpc{\char`\%}
\def\PYZdl{\char`\$}
\def\PYZhy{\char`\-}
\def\PYZsq{\char`\'}
\def\PYZdq{\char`\"}
\def\PYZti{\char`\~}
% for compatibility with earlier versions
\def\PYZat{@}
\def\PYZlb{[}
\def\PYZrb{]}
\makeatother


    % For linebreaks inside Verbatim environment from package fancyvrb. 
    \makeatletter
        \newbox\Wrappedcontinuationbox 
        \newbox\Wrappedvisiblespacebox 
        \newcommand*\Wrappedvisiblespace {\textcolor{red}{\textvisiblespace}} 
        \newcommand*\Wrappedcontinuationsymbol {\textcolor{red}{\llap{\tiny$\m@th\hookrightarrow$}}} 
        \newcommand*\Wrappedcontinuationindent {3ex } 
        \newcommand*\Wrappedafterbreak {\kern\Wrappedcontinuationindent\copy\Wrappedcontinuationbox} 
        % Take advantage of the already applied Pygments mark-up to insert 
        % potential linebreaks for TeX processing. 
        %        {, <, #, %, $, ' and ": go to next line. 
        %        _, }, ^, &, >, - and ~: stay at end of broken line. 
        % Use of \textquotesingle for straight quote. 
        \newcommand*\Wrappedbreaksatspecials {% 
            \def\PYGZus{\discretionary{\char`\_}{\Wrappedafterbreak}{\char`\_}}% 
            \def\PYGZob{\discretionary{}{\Wrappedafterbreak\char`\{}{\char`\{}}% 
            \def\PYGZcb{\discretionary{\char`\}}{\Wrappedafterbreak}{\char`\}}}% 
            \def\PYGZca{\discretionary{\char`\^}{\Wrappedafterbreak}{\char`\^}}% 
            \def\PYGZam{\discretionary{\char`\&}{\Wrappedafterbreak}{\char`\&}}% 
            \def\PYGZlt{\discretionary{}{\Wrappedafterbreak\char`\<}{\char`\<}}% 
            \def\PYGZgt{\discretionary{\char`\>}{\Wrappedafterbreak}{\char`\>}}% 
            \def\PYGZsh{\discretionary{}{\Wrappedafterbreak\char`\#}{\char`\#}}% 
            \def\PYGZpc{\discretionary{}{\Wrappedafterbreak\char`\%}{\char`\%}}% 
            \def\PYGZdl{\discretionary{}{\Wrappedafterbreak\char`\$}{\char`\$}}% 
            \def\PYGZhy{\discretionary{\char`\-}{\Wrappedafterbreak}{\char`\-}}% 
            \def\PYGZsq{\discretionary{}{\Wrappedafterbreak\textquotesingle}{\textquotesingle}}% 
            \def\PYGZdq{\discretionary{}{\Wrappedafterbreak\char`\"}{\char`\"}}% 
            \def\PYGZti{\discretionary{\char`\~}{\Wrappedafterbreak}{\char`\~}}% 
        } 
        % Some characters . , ; ? ! / are not pygmentized. 
        % This macro makes them "active" and they will insert potential linebreaks 
        \newcommand*\Wrappedbreaksatpunct {% 
            \lccode`\~`\.\lowercase{\def~}{\discretionary{\hbox{\char`\.}}{\Wrappedafterbreak}{\hbox{\char`\.}}}% 
            \lccode`\~`\,\lowercase{\def~}{\discretionary{\hbox{\char`\,}}{\Wrappedafterbreak}{\hbox{\char`\,}}}% 
            \lccode`\~`\;\lowercase{\def~}{\discretionary{\hbox{\char`\;}}{\Wrappedafterbreak}{\hbox{\char`\;}}}% 
            \lccode`\~`\:\lowercase{\def~}{\discretionary{\hbox{\char`\:}}{\Wrappedafterbreak}{\hbox{\char`\:}}}% 
            \lccode`\~`\?\lowercase{\def~}{\discretionary{\hbox{\char`\?}}{\Wrappedafterbreak}{\hbox{\char`\?}}}% 
            \lccode`\~`\!\lowercase{\def~}{\discretionary{\hbox{\char`\!}}{\Wrappedafterbreak}{\hbox{\char`\!}}}% 
            \lccode`\~`\/\lowercase{\def~}{\discretionary{\hbox{\char`\/}}{\Wrappedafterbreak}{\hbox{\char`\/}}}% 
            \catcode`\.\active
            \catcode`\,\active 
            \catcode`\;\active
            \catcode`\:\active
            \catcode`\?\active
            \catcode`\!\active
            \catcode`\/\active 
            \lccode`\~`\~ 	
        }
    \makeatother

    \let\OriginalVerbatim=\Verbatim
    \makeatletter
    \renewcommand{\Verbatim}[1][1]{%
        %\parskip\z@skip
        \sbox\Wrappedcontinuationbox {\Wrappedcontinuationsymbol}%
        \sbox\Wrappedvisiblespacebox {\FV@SetupFont\Wrappedvisiblespace}%
        \def\FancyVerbFormatLine ##1{\hsize\linewidth
            \vtop{\raggedright\hyphenpenalty\z@\exhyphenpenalty\z@
                \doublehyphendemerits\z@\finalhyphendemerits\z@
                \strut ##1\strut}%
        }%
        % If the linebreak is at a space, the latter will be displayed as visible
        % space at end of first line, and a continuation symbol starts next line.
        % Stretch/shrink are however usually zero for typewriter font.
        \def\FV@Space {%
            \nobreak\hskip\z@ plus\fontdimen3\font minus\fontdimen4\font
            \discretionary{\copy\Wrappedvisiblespacebox}{\Wrappedafterbreak}
            {\kern\fontdimen2\font}%
        }%
        
        % Allow breaks at special characters using \PYG... macros.
        \Wrappedbreaksatspecials
        % Breaks at punctuation characters . , ; ? ! and / need catcode=\active 	
        \OriginalVerbatim[#1,codes*=\Wrappedbreaksatpunct]%
    }
    \makeatother

    % Exact colors from NB
    \definecolor{incolor}{HTML}{303F9F}
    \definecolor{outcolor}{HTML}{D84315}
    \definecolor{cellborder}{HTML}{CFCFCF}
    \definecolor{cellbackground}{HTML}{F7F7F7}
    
    % prompt
    \makeatletter
    \newcommand{\boxspacing}{\kern\kvtcb@left@rule\kern\kvtcb@boxsep}
    \makeatother
    \newcommand{\prompt}[4]{
        {\ttfamily\llap{{\color{#2}[#3]:\hspace{3pt}#4}}\vspace{-\baselineskip}}
    }
    

    
    % Prevent overflowing lines due to hard-to-break entities
    \sloppy 
    % Setup hyperref package
    \hypersetup{
      breaklinks=true,  % so long urls are correctly broken across lines
      colorlinks=true,
      urlcolor=urlcolor,
      linkcolor=linkcolor,
      citecolor=citecolor,
      }
    % Slightly bigger margins than the latex defaults
    
    \geometry{verbose,tmargin=1in,bmargin=1in,lmargin=1in,rmargin=1in}
    
    

\begin{document}
    
    \maketitle
    
    

    
    \hypertarget{space-mechanics-eart-to-uranus}{%
\section{Space mechanics : Eart to
Uranus}\label{space-mechanics-eart-to-uranus}}

    \hypertarget{students-hugo-lancery---lucie-michelet---elss}{%
\paragraph{Students : Hugo LANCERY - Lucie MICHELET -
ELSS}\label{students-hugo-lancery---lucie-michelet---elss}}

    \begin{tcolorbox}[breakable, size=fbox, boxrule=1pt, pad at break*=1mm,colback=cellbackground, colframe=cellborder]
\prompt{In}{incolor}{1}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
\PY{k+kn}{import} \PY{n+nn}{numpy} \PY{k}{as} \PY{n+nn}{np}
\end{Verbatim}
\end{tcolorbox}

    \hypertarget{library}{%
\subsubsection{Library}\label{library}}

    \begin{tcolorbox}[breakable, size=fbox, boxrule=1pt, pad at break*=1mm,colback=cellbackground, colframe=cellborder]
\prompt{In}{incolor}{223}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
\PY{k}{def} \PY{n+nf}{param}\PY{p}{(}\PY{n}{mue}\PY{p}{,}\PY{n}{V}\PY{p}{,}\PY{n}{R}\PY{p}{,}\PY{n}{mod}\PY{p}{)}\PY{p}{:}
    \PY{l+s+sd}{\PYZdq{}\PYZdq{}\PYZdq{}}
\PY{l+s+sd}{    Parameters}
\PY{l+s+sd}{    \PYZhy{}\PYZhy{}\PYZhy{}\PYZhy{}\PYZhy{}\PYZhy{}\PYZhy{}\PYZhy{}\PYZhy{}\PYZhy{}}
\PY{l+s+sd}{    mue : reduced gravitational constant of the planet}
\PY{l+s+sd}{    V : Velocity of the spacecraft}
\PY{l+s+sd}{    R : radius}
\PY{l+s+sd}{    mod : elliptic or hyperbola }

\PY{l+s+sd}{    Returns}
\PY{l+s+sd}{    \PYZhy{}\PYZhy{}\PYZhy{}\PYZhy{}\PYZhy{}\PYZhy{}\PYZhy{}}
\PY{l+s+sd}{    a : apoapsis }
\PY{l+s+sd}{    e : eccentricity }
\PY{l+s+sd}{    w : total energy [km.s\PYZhy{}2]}
\PY{l+s+sd}{    t : orital period [s]}

\PY{l+s+sd}{    \PYZdq{}\PYZdq{}\PYZdq{}}
    \PY{k}{if} \PY{n}{mod} \PY{o}{==} \PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{e}\PY{l+s+s1}{\PYZsq{}} \PY{p}{:}
        \PY{n}{a} \PY{o}{=} \PY{o}{\PYZhy{}}\PY{n}{mue}\PY{o}{/}\PY{p}{(}\PY{l+m+mi}{2}\PY{o}{*}\PY{p}{(}\PY{n}{V}\PY{o}{*}\PY{o}{*}\PY{l+m+mi}{2}\PY{o}{/}\PY{l+m+mi}{2}\PY{o}{\PYZhy{}}\PY{n}{mue}\PY{o}{/}\PY{n}{R}\PY{p}{)}\PY{p}{)}
        \PY{n}{e} \PY{o}{=} \PY{o}{\PYZhy{}}\PY{n}{R}\PY{o}{/}\PY{n}{a}\PY{o}{+}\PY{l+m+mi}{1}
        \PY{n}{w} \PY{o}{=} \PY{o}{\PYZhy{}}\PY{n}{mue}\PY{o}{/}\PY{p}{(}\PY{l+m+mi}{2}\PY{o}{*}\PY{n}{a}\PY{p}{)}
    \PY{k}{if} \PY{n}{mod} \PY{o}{==} \PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{h}\PY{l+s+s1}{\PYZsq{}} \PY{p}{:}
        \PY{n}{a} \PY{o}{=} \PY{n}{mue}\PY{o}{/}\PY{p}{(}\PY{l+m+mi}{2}\PY{o}{*}\PY{p}{(}\PY{n}{V}\PY{o}{*}\PY{o}{*}\PY{l+m+mi}{2}\PY{o}{/}\PY{l+m+mi}{2}\PY{o}{\PYZhy{}}\PY{n}{mue}\PY{o}{/}\PY{n}{R}\PY{p}{)}\PY{p}{)}
        \PY{n}{e} \PY{o}{=} \PY{l+m+mi}{1}\PY{o}{+}\PY{n}{R}\PY{o}{/}\PY{n}{a}
        \PY{n}{w} \PY{o}{=} \PY{n}{mue}\PY{o}{/}\PY{p}{(}\PY{l+m+mi}{2}\PY{o}{*}\PY{n}{a}\PY{p}{)}
    \PY{n}{t} \PY{o}{=} \PY{l+m+mi}{2}\PY{o}{*}\PY{n}{np}\PY{o}{.}\PY{n}{pi}\PY{o}{*}\PY{n}{np}\PY{o}{.}\PY{n}{sqrt}\PY{p}{(}\PY{n}{a}\PY{o}{*}\PY{o}{*}\PY{l+m+mi}{3}\PY{o}{/}\PY{n}{mue}\PY{p}{)}
    \PY{k}{return} \PY{n}{a}\PY{p}{,}\PY{n}{e}\PY{p}{,}\PY{n}{w}\PY{p}{,}\PY{n}{t}

\PY{k}{def} \PY{n+nf}{Vl}\PY{p}{(}\PY{n}{mue}\PY{p}{,}\PY{n}{d}\PY{p}{)}\PY{p}{:}
    \PY{l+s+sd}{\PYZdq{}\PYZdq{}\PYZdq{}}
\PY{l+s+sd}{    Parameters}
\PY{l+s+sd}{    \PYZhy{}\PYZhy{}\PYZhy{}\PYZhy{}\PYZhy{}\PYZhy{}\PYZhy{}\PYZhy{}\PYZhy{}\PYZhy{}}
\PY{l+s+sd}{    mue : int \PYZhy{} gravitaional reduced param.}
\PY{l+s+sd}{    R : int \PYZhy{} distance}

\PY{l+s+sd}{    Returns}
\PY{l+s+sd}{    \PYZhy{}\PYZhy{}\PYZhy{}\PYZhy{}\PYZhy{}\PYZhy{}\PYZhy{}}
\PY{l+s+sd}{    float \PYZhy{} The velocity for liberation}
\PY{l+s+sd}{    \PYZdq{}\PYZdq{}\PYZdq{}}
    \PY{k}{return} \PY{n}{np}\PY{o}{.}\PY{n}{sqrt}\PY{p}{(}\PY{l+m+mi}{2}\PY{o}{*}\PY{n}{mue}\PY{o}{/}\PY{n}{d}\PY{p}{)}


\PY{k}{def} \PY{n+nf}{V}\PY{p}{(}\PY{n}{mue}\PY{p}{,}\PY{n}{R}\PY{p}{)}\PY{p}{:}
    \PY{k}{return} \PY{n}{np}\PY{o}{.}\PY{n}{sqrt}\PY{p}{(}\PY{n}{mue}\PY{o}{/}\PY{n}{R}\PY{p}{)}


\PY{k}{def} \PY{n+nf}{E\PYZus{}h}\PY{p}{(}\PY{n}{R}\PY{p}{,}\PY{n}{a}\PY{p}{,}\PY{n}{e}\PY{p}{)}\PY{p}{:}
    \PY{k}{return} \PY{n}{np}\PY{o}{.}\PY{n}{log}\PY{p}{(}\PY{p}{(}\PY{n}{Ro}\PY{o}{/}\PY{n}{a}\PY{o}{+}\PY{l+m+mi}{1}\PY{p}{)}\PY{o}{*}\PY{p}{(}\PY{n}{e}\PY{o}{*}\PY{o}{*}\PY{o}{\PYZhy{}}\PY{l+m+mi}{1}\PY{p}{)}\PY{o}{+}\PY{n}{np}\PY{o}{.}\PY{n}{sqrt}\PY{p}{(}\PY{p}{(}\PY{p}{(}\PY{n}{R}\PY{o}{/}\PY{n}{a}\PY{o}{+}\PY{l+m+mi}{1}\PY{p}{)}\PY{o}{*}\PY{n}{e}\PY{o}{*}\PY{o}{*}\PY{o}{\PYZhy{}}\PY{l+m+mi}{1}\PY{p}{)}\PY{o}{*}\PY{o}{*}\PY{l+m+mi}{2}\PY{o}{\PYZhy{}}\PY{l+m+mi}{1}\PY{p}{)}\PY{p}{)}

\PY{k}{def} \PY{n+nf}{t\PYZus{}tp\PYZus{}h}\PY{p}{(}\PY{n}{E}\PY{p}{,}\PY{n}{a}\PY{p}{,}\PY{n}{e}\PY{p}{,}\PY{n}{mue}\PY{p}{,}\PY{n}{tp}\PY{o}{=}\PY{l+m+mi}{0}\PY{p}{)}\PY{p}{:}
    \PY{c+c1}{\PYZsh{}/!\PYZbs{} E en radian pour les calculs}
    \PY{k}{return} \PY{p}{(}\PY{n}{np}\PY{o}{.}\PY{n}{sqrt}\PY{p}{(}\PY{n}{a}\PY{o}{*}\PY{o}{*}\PY{l+m+mi}{3}\PY{o}{/}\PY{n}{mue}\PY{p}{)}\PY{p}{)}\PY{o}{*}\PY{p}{(}\PY{n}{e}\PY{o}{*}\PY{n}{np}\PY{o}{.}\PY{n}{sinh}\PY{p}{(}\PY{n}{E}\PY{p}{)}\PY{o}{\PYZhy{}}\PY{n}{E}\PY{p}{)}\PY{o}{+}\PY{n}{tp}


\PY{k}{def} \PY{n+nf}{E\PYZus{}e}\PY{p}{(}\PY{n}{R}\PY{p}{,}\PY{n}{a}\PY{p}{,}\PY{n}{e}\PY{p}{)}\PY{p}{:}
    \PY{k}{return} \PY{n}{np}\PY{o}{.}\PY{n}{arccos}\PY{p}{(}\PY{p}{(}\PY{n}{R}\PY{o}{/}\PY{n}{a}\PY{o}{\PYZhy{}}\PY{l+m+mi}{1}\PY{p}{)}\PY{o}{/}\PY{p}{(}\PY{o}{\PYZhy{}}\PY{n}{e}\PY{p}{)}\PY{p}{)}

\PY{k}{def} \PY{n+nf}{t\PYZus{}tp\PYZus{}e}\PY{p}{(}\PY{n}{E}\PY{p}{,}\PY{n}{a}\PY{p}{,}\PY{n}{e}\PY{p}{,}\PY{n}{mue}\PY{p}{,}\PY{n}{tp}\PY{o}{=}\PY{l+m+mi}{0}\PY{p}{)}\PY{p}{:}
    \PY{k}{return} \PY{p}{(}\PY{n}{np}\PY{o}{.}\PY{n}{sqrt}\PY{p}{(}\PY{n}{a}\PY{o}{*}\PY{o}{*}\PY{l+m+mi}{3}\PY{o}{/}\PY{n}{mue}\PY{p}{)}\PY{p}{)}\PY{o}{*}\PY{p}{(}\PY{n}{E} \PY{o}{\PYZhy{}} \PY{n}{e}\PY{o}{*}\PY{n}{np}\PY{o}{.}\PY{n}{sin}\PY{p}{(}\PY{n}{E}\PY{p}{)}\PY{p}{)}\PY{o}{+}\PY{n}{tp}


\PY{k}{def} \PY{n+nf}{Vrot}\PY{p}{(}\PY{n}{R}\PY{p}{,}\PY{n}{T}\PY{p}{)}\PY{p}{:}
    \PY{k}{return} \PY{l+m+mi}{2}\PY{o}{*}\PY{n}{np}\PY{o}{.}\PY{n}{pi}\PY{o}{*}\PY{n}{R}\PY{o}{/}\PY{n}{T}


\PY{k}{def} \PY{n+nf}{Vs}\PY{p}{(}\PY{n}{V1}\PY{p}{,}\PY{n}{V2}\PY{p}{,}\PY{n}{angle}\PY{p}{)}\PY{p}{:}
    \PY{k}{return} \PY{n}{np}\PY{o}{.}\PY{n}{sqrt}\PY{p}{(}\PY{n}{V1}\PY{o}{*}\PY{o}{*}\PY{l+m+mi}{2}\PY{o}{+}\PY{n}{V2}\PY{o}{*}\PY{o}{*}\PY{l+m+mi}{2}\PY{o}{+}\PY{l+m+mi}{2}\PY{o}{*}\PY{n}{V1}\PY{o}{*}\PY{n}{V2}\PY{o}{*}\PY{n}{np}\PY{o}{.}\PY{n}{cos}\PY{p}{(}\PY{n}{angle}\PY{p}{)}\PY{p}{)}


\PY{k}{def} \PY{n+nf}{deltaV}\PY{p}{(}\PY{n}{V1}\PY{p}{,}\PY{n}{V2}\PY{p}{)}\PY{p}{:}
    \PY{k}{if} \PY{n}{V2} \PY{o}{\PYZgt{}} \PY{n}{V1} \PY{p}{:}
        \PY{n+nb}{print}\PY{p}{(}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{Thanks to Jupiter influence, we accelerated !}\PY{l+s+s2}{\PYZdq{}}\PY{p}{)}
        \PY{n}{deltaV} \PY{o}{=} \PY{n}{V2}\PY{o}{\PYZhy{}}\PY{n}{V1}
        
    \PY{k}{if} \PY{n}{V1} \PY{o}{\PYZgt{}} \PY{n}{V2} \PY{p}{:}
        \PY{n+nb}{print}\PY{p}{(}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{Thanks to Jupiter influence, we decelerated !}\PY{l+s+s2}{\PYZdq{}}\PY{p}{)}
        \PY{n}{deltaV} \PY{o}{=} \PY{n}{V1}\PY{o}{\PYZhy{}}\PY{n}{V2}
    
    \PY{k}{if} \PY{n}{V1} \PY{o}{==} \PY{n}{V2} \PY{p}{:}
        \PY{n+nb}{print}\PY{p}{(}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{Jupiter influence didn}\PY{l+s+s2}{\PYZsq{}}\PY{l+s+s2}{t affect the velocity of the spacecraft.}\PY{l+s+s2}{\PYZdq{}}\PY{p}{)}
        \PY{n}{deltaV} \PY{o}{=} \PY{l+m+mi}{0}
        
    \PY{k}{return} \PY{n}{deltaV}
\end{Verbatim}
\end{tcolorbox}

    \hypertarget{importation-of-the-data}{%
\subsubsection{Importation of the data}\label{importation-of-the-data}}

    \begin{tcolorbox}[breakable, size=fbox, boxrule=1pt, pad at break*=1mm,colback=cellbackground, colframe=cellborder]
\prompt{In}{incolor}{225}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
\PY{c+c1}{\PYZsh{}Constante gravitationelle}
\PY{n}{G} \PY{o}{=} \PY{l+m+mf}{6.67428}\PY{o}{*}\PY{l+m+mi}{10}\PY{o}{*}\PY{o}{*}\PY{p}{(}\PY{o}{\PYZhy{}}\PY{l+m+mi}{11}\PY{p}{)}

\PY{c+c1}{\PYZsh{} Masse [kg]}
\PY{n}{mT} \PY{o}{=} \PY{l+m+mf}{5.9737}\PY{o}{*}\PY{l+m+mi}{10}\PY{o}{*}\PY{o}{*}\PY{p}{(}\PY{l+m+mi}{24}\PY{p}{)}
\PY{n}{mU} \PY{o}{=} \PY{l+m+mf}{8.681}\PY{o}{*}\PY{l+m+mi}{10}\PY{o}{*}\PY{o}{*}\PY{p}{(}\PY{l+m+mi}{25}\PY{p}{)}

\PY{c+c1}{\PYZsh{} gravitational reduced param [km**3/s**2]}
\PY{n}{mueE} \PY{o}{=} \PY{n}{G}\PY{o}{*}\PY{n}{mT}\PY{o}{/}\PY{p}{(}\PY{l+m+mi}{1000}\PY{o}{*}\PY{o}{*}\PY{l+m+mi}{3}\PY{p}{)} 
\PY{n}{mueU} \PY{o}{=} \PY{n}{G}\PY{o}{*}\PY{n}{mU}\PY{o}{/}\PY{p}{(}\PY{l+m+mi}{1000}\PY{o}{*}\PY{o}{*}\PY{l+m+mi}{3}\PY{p}{)}
\PY{n}{mueS} \PY{o}{=} \PY{l+m+mf}{13.2}\PY{o}{*}\PY{l+m+mi}{10}\PY{o}{*}\PY{o}{*}\PY{l+m+mi}{10}
\PY{n}{mueJ} \PY{o}{=} \PY{l+m+mf}{126.5}\PY{o}{*}\PY{l+m+mi}{10}\PY{o}{*}\PY{o}{*}\PY{l+m+mi}{6}

\PY{c+c1}{\PYZsh{} distance au soleil}
\PY{n}{sJ} \PY{o}{=} \PY{l+m+mi}{750}\PY{o}{*}\PY{l+m+mi}{10}\PY{o}{*}\PY{o}{*}\PY{l+m+mi}{6}
\PY{n}{sU} \PY{o}{=} \PY{l+m+mf}{2.9}\PY{o}{*}\PY{l+m+mi}{10}\PY{o}{*}\PY{o}{*}\PY{l+m+mi}{9}
\PY{n}{sT} \PY{o}{=} \PY{l+m+mi}{150}\PY{o}{*}\PY{l+m+mi}{10}\PY{o}{*}\PY{o}{*}\PY{l+m+mi}{6}

\PY{c+c1}{\PYZsh{} Rayons en [km]}
\PY{n}{rT} \PY{o}{=} \PY{l+m+mi}{6878}
\PY{n}{rJ} \PY{o}{=} \PY{l+m+mi}{71400}
\PY{n}{rU} \PY{o}{=} \PY{l+m+mi}{25362} 
\PY{n}{h} \PY{o}{=} \PY{l+m+mi}{200}
\PY{n}{omgp} \PY{o}{=} \PY{n}{h} \PY{o}{+}\PY{n}{rT}
\end{Verbatim}
\end{tcolorbox}

    \hypertarget{initial-state}{%
\subsubsection{Initial State}\label{initial-state}}

    We calculate the velocity of satelization and liberation of our
satellite and its parameters

    \begin{tcolorbox}[breakable, size=fbox, boxrule=1pt, pad at break*=1mm,colback=cellbackground, colframe=cellborder]
\prompt{In}{incolor}{226}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
\PY{n}{vsat} \PY{o}{=} \PY{p}{(}\PY{n}{mueE}\PY{o}{/}\PY{n}{omgp}\PY{p}{)}\PY{o}{*}\PY{o}{*}\PY{l+m+mf}{0.5}
\PY{n}{vlib} \PY{o}{=} \PY{n}{Vl}\PY{p}{(}\PY{n}{mueE}\PY{p}{,}\PY{n}{omgp}\PY{p}{)}

\PY{c+c1}{\PYZsh{}param initial state}
\PY{n}{a} \PY{o}{=} \PY{o}{\PYZhy{}}\PY{n}{mueE}\PY{o}{/}\PY{p}{(}\PY{l+m+mi}{2}\PY{o}{*}\PY{p}{(}\PY{n}{vsat}\PY{o}{*}\PY{o}{*}\PY{l+m+mi}{2}\PY{o}{/}\PY{l+m+mi}{2}\PY{o}{\PYZhy{}}\PY{n}{mueE}\PY{o}{/}\PY{n}{omgp}\PY{p}{)}\PY{p}{)}
\PY{n}{e} \PY{o}{=} \PY{l+m+mi}{0}   \PY{c+c1}{\PYZsh{} because LEO}
\PY{n}{t} \PY{o}{=} \PY{l+m+mi}{2}\PY{o}{*}\PY{n}{np}\PY{o}{.}\PY{n}{pi}\PY{o}{*}\PY{n}{np}\PY{o}{.}\PY{n}{sqrt}\PY{p}{(}\PY{n}{a}\PY{o}{*}\PY{o}{*}\PY{l+m+mi}{3}\PY{o}{/}\PY{n}{mueE}\PY{p}{)}

\PY{n+nb}{print}\PY{p}{(}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{Satelization velocity : }\PY{l+s+s2}{\PYZdq{}}\PY{p}{,}\PY{n}{vsat}\PY{p}{,}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+se}{\PYZbs{}n}\PY{l+s+s2}{Liberation Velocity : }\PY{l+s+s2}{\PYZdq{}}\PY{p}{,}\PY{n}{vlib}\PY{p}{)}
\end{Verbatim}
\end{tcolorbox}

    \begin{Verbatim}[commandchars=\\\{\}]
Satelization velocity :  7.505310019652698
Liberation Velocity :  10.614111219607524
    \end{Verbatim}

    \hypertarget{first-tranfert-orbit---leaving-earth-inlfuence}{%
\subsubsection{First Tranfert Orbit - leaving Earth
inlfuence}\label{first-tranfert-orbit---leaving-earth-inlfuence}}

    Then we add velocity to exit the earth influence

    \begin{tcolorbox}[breakable, size=fbox, boxrule=1pt, pad at break*=1mm,colback=cellbackground, colframe=cellborder]
\prompt{In}{incolor}{227}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
\PY{c+c1}{\PYZsh{}acceleration to have an hyperbola}
\PY{n}{dv0} \PY{o}{=} \PY{l+m+mf}{6.66}
\PY{n}{v0} \PY{o}{=} \PY{n}{vsat} \PY{o}{+} \PY{n}{dv0}
\PY{n}{a0}\PY{p}{,}\PY{n}{e0}\PY{p}{,}\PY{n}{w0}\PY{p}{,}\PY{n}{T0} \PY{o}{=} \PY{n}{param}\PY{p}{(}\PY{n}{mueE}\PY{p}{,}\PY{n}{v0}\PY{p}{,}\PY{n}{omgp}\PY{p}{,}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{h}\PY{l+s+s1}{\PYZsq{}}\PY{p}{)}

\PY{n}{phi0} \PY{o}{=} \PY{n}{np}\PY{o}{.}\PY{n}{arccos}\PY{p}{(}\PY{l+m+mi}{1}\PY{o}{/}\PY{n}{e0}\PY{p}{)}\PY{o}{*}\PY{l+m+mi}{180}\PY{o}{/}\PY{n}{np}\PY{o}{.}\PY{n}{pi}

\PY{c+c1}{\PYZsh{}\PYZpc{}\PYZpc{} Calculation of time for entering jupiter area}

\PY{n}{Ro} \PY{o}{=} \PY{l+m+mi}{900000}
\PY{n}{tp} \PY{o}{=} \PY{l+m+mi}{0}

\PY{n}{E0} \PY{o}{=} \PY{n}{E\PYZus{}h}\PY{p}{(}\PY{n}{Ro}\PY{p}{,}\PY{n}{a0}\PY{p}{,}\PY{n}{e0}\PY{p}{)}
\PY{n}{E0deg} \PY{o}{=} \PY{n}{E0}\PY{o}{*}\PY{l+m+mi}{180}\PY{o}{/}\PY{n}{np}\PY{o}{.}\PY{n}{pi}

\PY{n}{t0} \PY{o}{=} \PY{n}{t\PYZus{}tp\PYZus{}h}\PY{p}{(}\PY{n}{E0}\PY{p}{,}\PY{n}{a0}\PY{p}{,}\PY{n}{e0}\PY{p}{,}\PY{n}{mueE}\PY{p}{,}\PY{n}{tp}\PY{p}{)} 
\PY{n+nb}{print}\PY{p}{(}\PY{n}{t0}\PY{o}{/}\PY{l+m+mi}{60}\PY{o}{/}\PY{l+m+mi}{60}\PY{p}{,}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{hours}\PY{l+s+s1}{\PYZsq{}}\PY{p}{)}

\PY{n}{n} \PY{o}{=} \PY{p}{(}\PY{n}{mueE}\PY{o}{/}\PY{p}{(}\PY{n}{a0}\PY{o}{*}\PY{o}{*}\PY{l+m+mi}{3}\PY{p}{)}\PY{p}{)}\PY{o}{*}\PY{o}{*}\PY{l+m+mf}{0.5} 
\end{Verbatim}
\end{tcolorbox}

    \begin{Verbatim}[commandchars=\\\{\}]
26.105181118306 hours
    \end{Verbatim}

    Now we want to know what is the velocity needed to enter jupiter
influence

    \begin{tcolorbox}[breakable, size=fbox, boxrule=1pt, pad at break*=1mm,colback=cellbackground, colframe=cellborder]
\prompt{In}{incolor}{228}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
\PY{c+c1}{\PYZsh{}velocity at limite of the earth influence sphere}
\PY{n}{VinfE} \PY{o}{=} \PY{n}{V}\PY{p}{(}\PY{n}{mueE}\PY{p}{,}\PY{n}{a0}\PY{p}{)}

\PY{n}{ua} \PY{o}{=} \PY{l+m+mi}{150}\PY{o}{*}\PY{l+m+mi}{10}\PY{o}{*}\PY{o}{*}\PY{l+m+mi}{6}
\PY{n}{TrotE} \PY{o}{=} \PY{l+m+mf}{365.25}\PY{o}{*}\PY{l+m+mi}{86400}


\PY{c+c1}{\PYZsh{}velocity rot earth}
\PY{n}{VrotE} \PY{o}{=} \PY{n}{Vrot}\PY{p}{(}\PY{n}{ua}\PY{p}{,}\PY{n}{TrotE}\PY{p}{)}

\PY{n}{angle\PYZus{}V\PYZus{}deg} \PY{o}{=} \PY{l+m+mf}{19.53}  
\PY{n}{angle\PYZus{}V} \PY{o}{=} \PY{l+m+mf}{19.53}\PY{o}{*}\PY{n}{np}\PY{o}{.}\PY{n}{pi}\PY{o}{/}\PY{l+m+mi}{180}

\PY{c+c1}{\PYZsh{}injection velocity }
\PY{n}{Vso} \PY{o}{=} \PY{n}{Vs}\PY{p}{(}\PY{n}{VinfE}\PY{p}{,}\PY{n}{VrotE}\PY{p}{,}\PY{n}{angle\PYZus{}V}\PY{p}{)}
\PY{n}{Vl1} \PY{o}{=} \PY{n}{Vl}\PY{p}{(}\PY{n}{mueS}\PY{p}{,}\PY{n}{ua}\PY{p}{)}
\PY{c+c1}{\PYZsh{} Vl1 \PYZgt{} Vso so we have an ellipse}

\PY{n+nb}{print}\PY{p}{(}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{Velocity needed : }\PY{l+s+s2}{\PYZdq{}}\PY{p}{,}\PY{n}{Vl1}\PY{p}{)}
\PY{n+nb}{print}\PY{p}{(}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{Velocity we have : }\PY{l+s+s2}{\PYZdq{}}\PY{p}{,}\PY{n}{Vso}\PY{p}{)}
\end{Verbatim}
\end{tcolorbox}

    \begin{Verbatim}[commandchars=\\\{\}]
Velocity needed :  41.95235392680606
Velocity we have :  38.83309985869477
    \end{Verbatim}

    We determine the date of rendez-vous with Jupiter

    \begin{tcolorbox}[breakable, size=fbox, boxrule=1pt, pad at break*=1mm,colback=cellbackground, colframe=cellborder]
\prompt{In}{incolor}{229}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
\PY{c+c1}{\PYZsh{}The parameter of the trajectory once the injection is done}
\PY{n}{a1}\PY{p}{,}\PY{n}{e1}\PY{p}{,}\PY{n}{w1}\PY{p}{,}\PY{n}{T1} \PY{o}{=} \PY{n}{param}\PY{p}{(}\PY{n}{mueS}\PY{p}{,}\PY{n}{Vso}\PY{p}{,}\PY{n}{ua}\PY{p}{,}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{e}\PY{l+s+s1}{\PYZsq{}}\PY{p}{)}
\end{Verbatim}
\end{tcolorbox}

    \begin{tcolorbox}[breakable, size=fbox, boxrule=1pt, pad at break*=1mm,colback=cellbackground, colframe=cellborder]
\prompt{In}{incolor}{230}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
\PY{n}{E1} \PY{o}{=} \PY{n}{E\PYZus{}e}\PY{p}{(}\PY{n}{sJ}\PY{p}{,}\PY{n}{a1}\PY{p}{,}\PY{n}{e1}\PY{p}{)}

\PY{n}{t1} \PY{o}{=} \PY{n}{t\PYZus{}tp\PYZus{}e}\PY{p}{(}\PY{n}{E1}\PY{p}{,}\PY{n}{a1}\PY{p}{,}\PY{n}{e1}\PY{p}{,}\PY{n}{mueS}\PY{p}{)}
\PY{n+nb}{print}\PY{p}{(}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{Time of transfer : }\PY{l+s+s2}{\PYZdq{}}\PY{p}{,}\PY{n}{t1}\PY{o}{/}\PY{l+m+mi}{60}\PY{o}{/}\PY{l+m+mi}{60}\PY{o}{/}\PY{l+m+mi}{24}\PY{o}{/}\PY{l+m+mi}{365}\PY{p}{,}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{year}\PY{l+s+s1}{\PYZsq{}}\PY{p}{)}
\end{Verbatim}
\end{tcolorbox}

    \begin{Verbatim}[commandchars=\\\{\}]
Time of transfer :  1.728999282487167 year
    \end{Verbatim}

    \begin{tcolorbox}[breakable, size=fbox, boxrule=1pt, pad at break*=1mm,colback=cellbackground, colframe=cellborder]
\prompt{In}{incolor}{231}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
\PY{c+c1}{\PYZsh{} Velocity jupiter to the sun}
\PY{n}{Vj} \PY{o}{=} \PY{n}{V}\PY{p}{(}\PY{n}{mueS}\PY{p}{,}\PY{n}{sJ}\PY{p}{)}
\PY{n+nb}{print}\PY{p}{(}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{Velocity of Jupiter : }\PY{l+s+s2}{\PYZdq{}}\PY{p}{,}\PY{n}{Vj}\PY{p}{)}
\end{Verbatim}
\end{tcolorbox}

    \begin{Verbatim}[commandchars=\\\{\}]
Velocity of Jupiter :  13.2664991614216
    \end{Verbatim}

    \begin{tcolorbox}[breakable, size=fbox, boxrule=1pt, pad at break*=1mm,colback=cellbackground, colframe=cellborder]
\prompt{In}{incolor}{232}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
\PY{c+c1}{\PYZsh{} velocity of the spacecraft, related to Sun, at the level of Jupiter orbit and the angle of crossing orbit directions}
   
\PY{n}{Vs1} \PY{o}{=} \PY{n}{np}\PY{o}{.}\PY{n}{sqrt}\PY{p}{(}\PY{l+m+mi}{2}\PY{o}{*}\PY{p}{(}\PY{o}{\PYZhy{}}\PY{n}{mueS}\PY{o}{/}\PY{p}{(}\PY{l+m+mi}{2}\PY{o}{*}\PY{n}{a1}\PY{p}{)}\PY{o}{+}\PY{n}{mueS}\PY{o}{/}\PY{n}{sJ}\PY{p}{)}\PY{p}{)}   \PY{c+c1}{\PYZsh{}[km/s]}
\PY{n}{phi1} \PY{o}{=} \PY{n}{np}\PY{o}{.}\PY{n}{arccos}\PY{p}{(}\PY{n}{Vso}\PY{o}{*}\PY{n}{ua}\PY{o}{/}\PY{p}{(}\PY{n}{Vs1}\PY{o}{*}\PY{n}{sJ}\PY{p}{)}\PY{p}{)}
\PY{n}{phi1deg} \PY{o}{=} \PY{n}{phi1}\PY{o}{*}\PY{l+m+mi}{180}\PY{o}{/}\PY{n}{np}\PY{o}{.}\PY{n}{pi}

\PY{n+nb}{print}\PY{p}{(}\PY{n}{Vs1}\PY{p}{)}
\end{Verbatim}
\end{tcolorbox}

    \begin{Verbatim}[commandchars=\\\{\}]
10.000482220141187
    \end{Verbatim}

    \begin{tcolorbox}[breakable, size=fbox, boxrule=1pt, pad at break*=1mm,colback=cellbackground, colframe=cellborder]
\prompt{In}{incolor}{233}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
\PY{c+c1}{\PYZsh{} velocity of the spacecraft, related to Jupiter, at the entry point and the angle}

\PY{n}{Vinf1} \PY{o}{=} \PY{n}{np}\PY{o}{.}\PY{n}{sqrt}\PY{p}{(}\PY{n}{Vs1}\PY{o}{*}\PY{o}{*}\PY{l+m+mi}{2}\PY{o}{+}\PY{n}{Vj}\PY{o}{*}\PY{o}{*}\PY{l+m+mi}{2}\PY{o}{\PYZhy{}}\PY{l+m+mi}{2}\PY{o}{*}\PY{n}{Vs1}\PY{o}{*}\PY{n}{Vj}\PY{o}{*}\PY{n}{np}\PY{o}{.}\PY{n}{cos}\PY{p}{(}\PY{n}{phi1}\PY{p}{)}\PY{p}{)}
\PY{n}{alpha1} \PY{o}{=} \PY{n}{np}\PY{o}{.}\PY{n}{arcsin}\PY{p}{(}\PY{n}{np}\PY{o}{.}\PY{n}{sin}\PY{p}{(}\PY{n}{phi1}\PY{p}{)}\PY{o}{/}\PY{n}{Vinf1}\PY{o}{*}\PY{n}{Vs1}\PY{p}{)}
\PY{n}{alpha1deg} \PY{o}{=} \PY{n}{alpha1}\PY{o}{*}\PY{l+m+mi}{180}\PY{o}{/}\PY{n}{np}\PY{o}{.}\PY{n}{pi}

\PY{n+nb}{print}\PY{p}{(}\PY{n}{Vinf1}\PY{p}{)}
\end{Verbatim}
\end{tcolorbox}

    \begin{Verbatim}[commandchars=\\\{\}]
8.36289004776757
    \end{Verbatim}

    \hypertarget{arrival-in-the-jupiter-neighborhood}{%
\subsubsection{Arrival in the Jupiter
neighborhood}\label{arrival-in-the-jupiter-neighborhood}}

    We determine the following parameters of the flyby trajectory at 50000
km altitude

    \begin{tcolorbox}[breakable, size=fbox, boxrule=1pt, pad at break*=1mm,colback=cellbackground, colframe=cellborder]
\prompt{In}{incolor}{285}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
\PY{n}{h1} \PY{o}{=} \PY{l+m+mf}{0.18}\PY{o}{*}\PY{n}{rJ}
\PY{n}{Rj} \PY{o}{=} \PY{n}{rJ}\PY{o}{+}\PY{n}{h1}        

\PY{n}{aj} \PY{o}{=} \PY{n}{mueJ}\PY{o}{/}\PY{p}{(}\PY{n}{Vinf1}\PY{o}{*}\PY{o}{*}\PY{l+m+mi}{2}\PY{p}{)}
\PY{n}{ej} \PY{o}{=} \PY{l+m+mi}{1}\PY{o}{+}\PY{n}{Rj}\PY{o}{/}\PY{n}{aj}
\PY{n}{phij} \PY{o}{=} \PY{n}{np}\PY{o}{.}\PY{n}{arccos}\PY{p}{(}\PY{l+m+mi}{1}\PY{o}{/}\PY{n}{ej}\PY{p}{)}
\PY{n}{phijdeg} \PY{o}{=} \PY{n}{phij}\PY{o}{*}\PY{l+m+mi}{180}\PY{o}{/}\PY{n}{np}\PY{o}{.}\PY{n}{pi}

\PY{n}{alphajdeg} \PY{o}{=} \PY{l+m+mi}{180}\PY{o}{\PYZhy{}}\PY{l+m+mi}{2}\PY{o}{*}\PY{n}{phijdeg}\PY{o}{\PYZhy{}}\PY{n}{alpha1deg}
\PY{n}{alphaj} \PY{o}{=} \PY{n}{alphajdeg}\PY{o}{*}\PY{n}{np}\PY{o}{.}\PY{n}{pi}\PY{o}{/}\PY{l+m+mi}{180}
\end{Verbatim}
\end{tcolorbox}

    Now we want to determine the exit conditions of the Jovian sphere

    \begin{tcolorbox}[breakable, size=fbox, boxrule=1pt, pad at break*=1mm,colback=cellbackground, colframe=cellborder]
\prompt{In}{incolor}{286}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
\PY{c+c1}{\PYZsh{} velocity of the spacecraft, related to Sun, at the Jovian exit point and its angle}

\PY{n}{Vs2} \PY{o}{=} \PY{n}{Vs}\PY{p}{(}\PY{n}{Vinf1}\PY{p}{,}\PY{n}{Vj}\PY{p}{,}\PY{n}{alphaj}\PY{p}{)}
\PY{n}{phi2} \PY{o}{=} \PY{n}{np}\PY{o}{.}\PY{n}{arccos}\PY{p}{(}\PY{l+m+mi}{1}\PY{o}{/}\PY{p}{(}\PY{l+m+mi}{1}\PY{o}{+}\PY{n}{Rj}\PY{o}{/}\PY{p}{(}\PY{n}{mueJ}\PY{o}{/}\PY{p}{(}\PY{n}{Vs2}\PY{o}{*}\PY{o}{*}\PY{l+m+mi}{2}\PY{p}{)}\PY{p}{)}\PY{p}{)}\PY{p}{)}

\PY{n}{dV} \PY{o}{=} \PY{n}{deltaV}\PY{p}{(}\PY{n}{Vs1}\PY{p}{,}\PY{n}{Vs2}\PY{p}{)}

\PY{n+nb}{print}\PY{p}{(}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+se}{\PYZbs{}n}\PY{l+s+s2}{Velocity at the Jovian exit point : }\PY{l+s+s2}{\PYZdq{}}\PY{p}{,}\PY{n}{Vs2}\PY{p}{,}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+se}{\PYZbs{}n}\PY{l+s+s2}{Phi angle : }\PY{l+s+s2}{\PYZdq{}}\PY{p}{,}\PY{n}{phi2}\PY{o}{*}\PY{l+m+mi}{180}\PY{o}{/}\PY{n}{np}\PY{o}{.}\PY{n}{pi}\PY{p}{)}
\end{Verbatim}
\end{tcolorbox}

    \begin{Verbatim}[commandchars=\\\{\}]
Thanks to Jupiter influence, we accelerated !

Velocity at the Jovian exit point :  14.820537467937143
Phi angle :  29.263737168029998
    \end{Verbatim}

    \hypertarget{second-transfert-orbit-leaving-jupiter-influence}{%
\subsubsection{Second Transfert Orbit : leaving Jupiter
influence}\label{second-transfert-orbit-leaving-jupiter-influence}}
By hypothesis, the heliocentric orbit at the exit point of Jupiter influence sphere are:
r = sJ 
v = Vs2
phi = phi2 = 32.65°
    We determine the parameters of the new orbit

    \begin{tcolorbox}[breakable, size=fbox, boxrule=1pt, pad at break*=1mm,colback=cellbackground, colframe=cellborder]
\prompt{In}{incolor}{280}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
\PY{n}{Vl2} \PY{o}{=} \PY{n}{Vl}\PY{p}{(}\PY{n}{mueS}\PY{p}{,}\PY{n}{sJ}\PY{p}{)}
\PY{n+nb}{print}\PY{p}{(}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{Velocity needed to leave Jupiter influence :}\PY{l+s+s2}{\PYZdq{}}\PY{p}{,}\PY{n}{Vl2}\PY{p}{)}

\PY{c+c1}{\PYZsh{}Vs2\PYZlt{}Vl2 so ellipse}
\end{Verbatim}
\end{tcolorbox}

    \begin{Verbatim}[commandchars=\\\{\}]
Velocity needed to leave Jupiter influence : 18.76166303929372
    \end{Verbatim}

    \begin{tcolorbox}[breakable, size=fbox, boxrule=1pt, pad at break*=1mm,colback=cellbackground, colframe=cellborder]
\prompt{In}{incolor}{298}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
\PY{c+c1}{\PYZsh{}We add velocity to have an hyperbola}
\PY{n}{dv3} \PY{o}{=}  \PY{l+m+mf}{3.98}
\PY{n}{Vs3} \PY{o}{=} \PY{n}{Vs2} \PY{o}{+} \PY{n}{dv3}

\PY{c+c1}{\PYZsh{}Vs3\PYZgt{}Vl2}
\PY{n}{a3}\PY{p}{,}\PY{n}{e3}\PY{p}{,}\PY{n}{w3}\PY{p}{,}\PY{n}{T3} \PY{o}{=} \PY{n}{param}\PY{p}{(}\PY{n}{mueS}\PY{p}{,}\PY{n}{Vs3}\PY{p}{,}\PY{n}{sJ}\PY{p}{,}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{h}\PY{l+s+s1}{\PYZsq{}}\PY{p}{)}

\PY{n+nb}{print}\PY{p}{(}\PY{n}{e3}\PY{p}{)}
\end{Verbatim}
\end{tcolorbox}

    \begin{Verbatim}[commandchars=\\\{\}]
1.0082966425187976
    \end{Verbatim}

    We calculate the time of rendez vous with Uranus

    \begin{tcolorbox}[breakable, size=fbox, boxrule=1pt, pad at break*=1mm,colback=cellbackground, colframe=cellborder]
\prompt{In}{incolor}{299}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
\PY{n}{E3} \PY{o}{=} \PY{n}{E\PYZus{}h}\PY{p}{(}\PY{n}{sU}\PY{p}{,}\PY{n}{a3}\PY{p}{,}\PY{n}{e3}\PY{p}{)}
\PY{n}{t3} \PY{o}{=} \PY{n}{t\PYZus{}tp\PYZus{}h}\PY{p}{(}\PY{n}{E3}\PY{p}{,}\PY{n}{a3}\PY{p}{,}\PY{n}{e3}\PY{p}{,}\PY{n}{mueS}\PY{p}{)}

\PY{n+nb}{print}\PY{p}{(}\PY{n}{t3}\PY{o}{/}\PY{l+m+mi}{60}\PY{o}{/}\PY{l+m+mi}{60}\PY{o}{/}\PY{l+m+mi}{24}\PY{o}{/}\PY{l+m+mi}{365}\PY{p}{,}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{years}\PY{l+s+s2}{\PYZdq{}}\PY{p}{)}
\end{Verbatim}
\end{tcolorbox}

    \begin{Verbatim}[commandchars=\\\{\}]
6.531318218837246 years
    \end{Verbatim}

    \hypertarget{total-time}{%
\subsubsection{Total time}\label{total-time}}

    \begin{tcolorbox}[breakable, size=fbox, boxrule=1pt, pad at break*=1mm,colback=cellbackground, colframe=cellborder]
\prompt{In}{incolor}{300}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
\PY{n+nb}{print}\PY{p}{(}\PY{p}{(}\PY{n}{t0}\PY{o}{+}\PY{n}{t1}\PY{o}{+}\PY{n}{t3}\PY{p}{)}\PY{o}{/}\PY{l+m+mi}{60}\PY{o}{/}\PY{l+m+mi}{60}\PY{o}{/}\PY{l+m+mi}{24}\PY{o}{/}\PY{l+m+mi}{365}\PY{p}{)}
\end{Verbatim}
\end{tcolorbox}

    \begin{Verbatim}[commandchars=\\\{\}]
8.263297544831067
    \end{Verbatim}

    \hypertarget{arrival-on-uranus}{%
\subsubsection{Arrival on Uranus}\label{arrival-on-uranus}}

    \begin{tcolorbox}[breakable, size=fbox, boxrule=1pt, pad at break*=1mm,colback=cellbackground, colframe=cellborder]
\prompt{In}{incolor}{301}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
\PY{c+c1}{\PYZsh{} Velocity Uranus}
\PY{n}{Vu} \PY{o}{=} \PY{n}{V}\PY{p}{(}\PY{n}{mueS}\PY{p}{,}\PY{n}{sU}\PY{p}{)}
\PY{n+nb}{print}\PY{p}{(}\PY{n}{Vu}\PY{p}{)}
\end{Verbatim}
\end{tcolorbox}

    \begin{Verbatim}[commandchars=\\\{\}]
6.7466466766320545
    \end{Verbatim}

    \begin{tcolorbox}[breakable, size=fbox, boxrule=1pt, pad at break*=1mm,colback=cellbackground, colframe=cellborder]
\prompt{In}{incolor}{302}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
\PY{c+c1}{\PYZsh{} velocity of the spacecraft, related to Sun, at the level of Uranus orbit and the angle of crossing orbit directions}
\PY{n}{Vs4} \PY{o}{=} \PY{n}{np}\PY{o}{.}\PY{n}{sqrt}\PY{p}{(}\PY{l+m+mi}{2}\PY{o}{*}\PY{p}{(}\PY{o}{\PYZhy{}}\PY{n}{mueS}\PY{o}{/}\PY{p}{(}\PY{l+m+mi}{2}\PY{o}{*}\PY{n}{a3}\PY{p}{)}\PY{o}{+}\PY{n}{mueS}\PY{o}{/}\PY{n}{sU}\PY{p}{)}\PY{p}{)}   \PY{c+c1}{\PYZsh{}[km/s]}
\PY{n}{phi3} \PY{o}{=} \PY{n}{np}\PY{o}{.}\PY{n}{arccos}\PY{p}{(}\PY{n}{Vs3}\PY{o}{*}\PY{n}{sJ}\PY{o}{/}\PY{p}{(}\PY{n}{Vs4}\PY{o}{*}\PY{n}{sU}\PY{p}{)}\PY{p}{)}
\PY{n}{phi3deg} \PY{o}{=} \PY{n}{phi3}\PY{o}{*}\PY{l+m+mi}{180}\PY{o}{/}\PY{n}{np}\PY{o}{.}\PY{n}{pi}

\PY{n+nb}{print}\PY{p}{(}\PY{n}{Vs4}\PY{p}{)}
\end{Verbatim}
\end{tcolorbox}

    \begin{Verbatim}[commandchars=\\\{\}]
9.4643686358527
    \end{Verbatim}

    \begin{tcolorbox}[breakable, size=fbox, boxrule=1pt, pad at break*=1mm,colback=cellbackground, colframe=cellborder]
\prompt{In}{incolor}{303}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
\PY{c+c1}{\PYZsh{} velocity of the spacecraft, related to Uranus, at the entry point and the angle}
\PY{n}{Vinf4} \PY{o}{=} \PY{n}{Vs}\PY{p}{(}\PY{n}{Vs4}\PY{p}{,}\PY{n}{Vu}\PY{p}{,}\PY{n}{phi3}\PY{p}{)}
\PY{n+nb}{print}\PY{p}{(}\PY{n}{Vinf4}\PY{p}{)}
\end{Verbatim}
\end{tcolorbox}

    \begin{Verbatim}[commandchars=\\\{\}]
14.16681733779178
    \end{Verbatim}

    \begin{tcolorbox}[breakable, size=fbox, boxrule=1pt, pad at break*=1mm,colback=cellbackground, colframe=cellborder]
\prompt{In}{incolor}{304}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
\PY{c+c1}{\PYZsh{}Defining the orbit altitude}
\PY{n}{h3} \PY{o}{=} \PY{l+m+mi}{12000}
\PY{n}{Ru} \PY{o}{=} \PY{n}{rU}\PY{o}{+}\PY{n}{h3}  
\end{Verbatim}
\end{tcolorbox}

    \begin{tcolorbox}[breakable, size=fbox, boxrule=1pt, pad at break*=1mm,colback=cellbackground, colframe=cellborder]
\prompt{In}{incolor}{305}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
\PY{c+c1}{\PYZsh{}Satelization velocity of Uranus}
\PY{n}{VsatU} \PY{o}{=} \PY{n}{np}\PY{o}{.}\PY{n}{sqrt}\PY{p}{(}\PY{n}{mueU}\PY{o}{/}\PY{n}{Ru}\PY{p}{)}
\PY{n+nb}{print}\PY{p}{(}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{Vsat Uranus :}\PY{l+s+s2}{\PYZdq{}}\PY{p}{,}\PY{n}{VsatU}\PY{p}{)}
\end{Verbatim}
\end{tcolorbox}

    \begin{Verbatim}[commandchars=\\\{\}]
Vsat Uranus : 12.452943887539027
    \end{Verbatim}

    \begin{tcolorbox}[breakable, size=fbox, boxrule=1pt, pad at break*=1mm,colback=cellbackground, colframe=cellborder]
\prompt{In}{incolor}{306}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
\PY{c+c1}{\PYZsh{}Liberation velocity of Uranus}
\PY{n}{VlU} \PY{o}{=} \PY{n}{Vl}\PY{p}{(}\PY{n}{mueU}\PY{p}{,}\PY{n}{Ru}\PY{p}{)}
\PY{n+nb}{print}\PY{p}{(}\PY{n}{VlU}\PY{p}{)}
\end{Verbatim}
\end{tcolorbox}

    \begin{Verbatim}[commandchars=\\\{\}]
17.611122137228826
    \end{Verbatim}

    \begin{tcolorbox}[breakable, size=fbox, boxrule=1pt, pad at break*=1mm,colback=cellbackground, colframe=cellborder]
\prompt{In}{incolor}{308}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
\PY{c+c1}{\PYZsh{}Vinf4 \PYZlt{} VlU = ellipse}
\PY{n}{aU}\PY{p}{,}\PY{n}{eU}\PY{p}{,}\PY{n}{wU}\PY{p}{,}\PY{n}{Tu} \PY{o}{=} \PY{n}{param}\PY{p}{(}\PY{n}{mueU}\PY{p}{,}\PY{n}{Vinf4}\PY{p}{,}\PY{n}{Ru}\PY{p}{,}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{e}\PY{l+s+s1}{\PYZsq{}}\PY{p}{)}

\PY{n+nb}{print}\PY{p}{(}\PY{n}{eU}\PY{p}{)}\PY{c+c1}{\PYZsh{}ellipse}
\end{Verbatim}
\end{tcolorbox}

    \begin{Verbatim}[commandchars=\\\{\}]
0.29419740954318563
    \end{Verbatim}

    The velocity of the stalletite is between the satellization velocity and
the liberation velocity. We are in orbit around Uranus. We don't need to
add velocity to have an orbit around Uranus !

    \hypertarget{calculation-of-the-cost}{%
\subsubsection{Calculation of the cost}\label{calculation-of-the-cost}}

    \begin{tcolorbox}[breakable, size=fbox, boxrule=1pt, pad at break*=1mm,colback=cellbackground, colframe=cellborder]
\prompt{In}{incolor}{309}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
\PY{n}{dvTot} \PY{o}{=} \PY{n}{dv0}\PY{o}{+}\PY{n}{dv3} 
\PY{n+nb}{print}\PY{p}{(}\PY{n}{dvTot}\PY{p}{)}
\end{Verbatim}
\end{tcolorbox}

    \begin{Verbatim}[commandchars=\\\{\}]
10.64
    \end{Verbatim}

    We have a final coast of 10.64 km/s

    \begin{tcolorbox}[breakable, size=fbox, boxrule=1pt, pad at break*=1mm,colback=cellbackground, colframe=cellborder]
\prompt{In}{incolor}{315}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
\PY{n}{m} \PY{o}{=} \PY{l+m+mi}{12}
\PY{n}{ISP} \PY{o}{=} \PY{l+m+mi}{230}
\PY{c+c1}{\PYZsh{}solid ergol}

\PY{n}{Ec} \PY{o}{=} \PY{l+m+mf}{0.5}\PY{o}{*}\PY{n}{m}\PY{o}{*}\PY{n}{dvTot}\PY{o}{*}\PY{o}{*}\PY{l+m+mi}{2}
\PY{n+nb}{print}\PY{p}{(}\PY{n}{Ec}\PY{p}{,}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{N}\PY{l+s+s2}{\PYZdq{}}\PY{p}{)}

\PY{n}{conso} \PY{o}{=} \PY{n}{Ec}\PY{o}{/}\PY{p}{(}\PY{n}{ISP}\PY{p}{)}
\PY{n+nb}{print}\PY{p}{(}\PY{n}{conso}\PY{p}{,}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{kg/s}\PY{l+s+s2}{\PYZdq{}}\PY{p}{)}

\PY{c+c1}{\PYZsh{}print(\PYZdq{}total conso : \PYZdq{})}
\end{Verbatim}
\end{tcolorbox}

    \begin{Verbatim}[commandchars=\\\{\}]
679.2576 N
2.9532939130434785 kg/s
    \end{Verbatim}

    \begin{tcolorbox}[breakable, size=fbox, boxrule=1pt, pad at break*=1mm,colback=cellbackground, colframe=cellborder]
\prompt{In}{incolor}{ }{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]

\end{Verbatim}
\end{tcolorbox}


    % Add a bibliography block to the postdoc
    
    
    
\end{document}
