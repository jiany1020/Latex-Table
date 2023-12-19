# Latex-Table
How to create a latex table with sd right below the mean with stars automatically added just like the picture below?
<img width="384" alt="image" src="https://github.com/jiany1020/Latex-Table/assets/146483814/f21eb148-7473-434d-a051-bd96be404c86">

Here is the code:
```
\documentclass{article}
\usepackage{booktabs} % For formal tables

% Define a new command for formatting the p-values with stars
\newcommand{\pvalue}[1]{%
  $ #1 $%
  \ifdim #1 pt < 0.05pt %
    \rlap{**}%
  \else
    \ifdim #1 pt < 0.1pt %
      \rlap{*}%
    \fi
  \fi
}

\begin{document}

\begin{table}[h]
\centering
\caption{Updated Descriptive Statistics and T-Test P-Values}
\begin{tabular}{@{}lcccccc@{}}
\toprule
& \multicolumn{3}{c}{Means and Standard Deviations} & \multicolumn{3}{c}{T-test of difference (p-value)} \\
\cmidrule(lr){2-4} \cmidrule(lr){5-7}
Variable & T1 & T2 & C & T1\_T2 & T1\_C & T2\_C \\ 
\midrule
loantaken & 
$0.53$ & $0.60$ & $0.49$ & \pvalue{0.19} & \pvalue{0.44} & \pvalue{0.04} \\
& $(0.50)$ & $(0.49)$ & $(0.50)$ & & & \\
num\_children & 
$0.86$ & $0.76$ & $0.70$ & \pvalue{0.39} & \pvalue{0.11} & \pvalue{0.56} \\
& $(0.99)$ & $(1.14)$ & $(0.91)$ & & & \\
education & 
$5.27$ & $5.40$ & $4.88$ & \pvalue{0.59} & \pvalue{0.13} & \pvalue{0.30} \\
& $(2.41)$ & $(2.42)$ & $(2.52)$ & & & \\
health\_satisfied & 
$3.88$ & $3.83$ & $3.83$ & \pvalue{0.60} & \pvalue{0.54} & \pvalue{0.95} \\
& $(0.75)$ & $(0.80)$ & $(0.73)$ & & & \\
hh\_contam\_count & 
$1.06$ & $1.02$ & $1.10$ & \pvalue{0.60} & \pvalue{0.56} & \pvalue{0.14} \\
& $(0.58)$ & $(0.69)$ & $(0.59)$ & & & \\
\midrule
N & 355 & 352 & 351 \\
\bottomrule
\end{tabular}
\end{table}

\end{document}
```
