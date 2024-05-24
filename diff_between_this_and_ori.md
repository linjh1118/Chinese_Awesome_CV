#### awesome-cv.cls ####

1. 修改summary和个人介绍的差距 xx mm
\newcommand{\acvHeaderAfterQuoteSkip}{-5mm}

2. 将姓名改小:xx.pt
\newcommand*{\headerfirstnamestyle}[1]{{\fontsize{16pt}{1em}\headerfontlight\color{graytext} #1}}
\newcommand*{\headerlastnamestyle}[1]{{\fontsize{16pt}{1em}\headerfont\bfseries\color{text} #1}}

3. 将图片改小
\newcommand*{\makecvheader}[1][C]{%
  \newcommand*{\drawphoto}{%
    \ifthenelse{\isundefined{\@photo}}{}{%
      \newlength{\photodim}
      \ifthenelse{\equal{\@photoshape}{circle}}%
        {\setlength{\photodim}{1.3cm}}
        {\setlength{\photodim}{1.8cm}}
修改两个xx.cm

4. 增加对微信的支持
定义新指令
\newcommand*{\wechat}[1]{\def\@wechat{#1}}

在headtext中注册微信图标
% linjh
      \ifthenelse{\isundefined{\@wechat}}%
        {}%
        {%
          \ifbool{isstart}{\setbool{isstart}{false}}{\acvHeaderSocialSep}%
          \href{https://github.com/linjh1118/WisdoMentor/blob/main/resources/wechat.jpg}{\faWechat\acvHeaderIconSep\@wechat}%
        }%
      % linjh


5. 定义一个新指令：cventryfour，在education中使用。从而不必强硬加上教育中的内容
\newcommand*{\cventryfour}[4]{%
  \vspace{-2.0mm}
  \setlength\tabcolsep{0pt}
  \setlength{\extrarowheight}{0pt}
  \begin{tabular*}{\textwidth}{@{\extracolsep{\fill}} L{\textwidth - 4.5cm} R{4.5cm}}
    \ifempty{#2#3}
      {\entrypositionstyle{#1} & \entrydatestyle{#4} \\}
      {\entrytitlestyle{#2} & \entrylocationstyle{#3} \\
      \entrypositionstyle{#1} & \entrydatestyle{#4} \\}
  \end{tabular*}%
}

#### resume.tex ####
1. 首先需要增加对中文的支持，在resume.tex的documentclass后一行加入\usepackage{xeCJK}
\documentclass[11pt, a4paper]{awesome-cv}
\usepackage{xeCJK}