---
title: "Columns, Tables, and Templates"
teaching: 0
exercises: 0
questions:
- "Key question: How can I add tabular data to a LaTeX document?"
- "Key question: How can I organize my text into columns?"
- "Key question: How can I use existing LaTeX templates to style my document in accordance with publisher or organization guidelines?
objectives:
- "First learning objective. "
- "Second learning objective. "
- "Third learning objective. "
keypoints:
- "First key point. "
- "Second key point."
- "Third key point. "
- "Fourth key point. "
---

### Tables & tabular data

Manually marking up tables in a LaTeX document can be a time-consuming task. It's often a better bet to begin by exporting your tabular data from another source and then copying/pasting the LaTeX code that those tools generate into your LaTeX document. You can generate LaTeX tables, for example, using:
- .to_latex() in pandas/Python
- stargazer for R
- excel2latex for Excel
- tablesgenerator.com and latex-tables.com are two online tools for generating LaTeX table markup



```latex
% in brawl_at_allen.tex
\usepackage{graphicx}

...

\chapter{The Banquet}

\includegraphics[]{troubadour}
```


```latex
\begin{figure}
    \centering
    \includegraphics[]{troubadour}
    \caption{A troubadour, performing}
    \label{fig:troubadour}
\end{figure}
```



## Columns

## LaTeX templates

> ## Challenge 1
>
> Will this code insert an image at a fixed location, or one whose location is flexible?
>
> ```latex
> \includegraphics[scale=.7]{constellations}
> ```
>
> > ## Answer
> > This code will insert an image whose location is fixed because it is not inside a floating environment.
> > {: .tex}
> {: .solution}
{: .challenge}

>
> ## Challenge 2
> `\includegraphics[]{}` has many different options it can take. Apply the `angle` option to the first image
> we added; its value should be a whole number between 0 and 360. You can also try this with the other images;
> multiple options are specified as a comma-separated list.
>
> > ## Answer
> > ```latex
> > \begin{figure}
> >     \centering
> >     \includegraphics[angle=30]{troubadour}
> >     \caption{A troubadour, performing}
> >     \label{fig:troubadour}
> > \end{figure}
> > ```
> > {: .tex}
> {: .solution}
{: .challenge}
