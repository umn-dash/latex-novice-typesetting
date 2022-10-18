---
title: "Columns, Tables, and Templates"
teaching: 0
exercises: 0
questions:
- "Key question: How can I add tabular data to a LaTeX document?"
- "Key question: How can I organize my text into columns?"
- "Key question: How can I use existing LaTeX templates to style my document in accordance with publisher or organization guidelines?"
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

Manually marking up tables in a LaTeX document can be a time-consuming task. It's often a better idea to begin by exporting your tabular data from another source and then copying/pasting the LaTeX code that those tools generate into your LaTeX document. You can generate LaTeX tables using tools like:
- .to_latex() in pandas/Python
- stargazer for R
- excel2latex for Excel
- tablesgenerator.com 
- latex-tables.com 

But we can create a simple table in LaTeX directly, so that we will better understand the general structure. First, we want to use the `tabular` environment in LaTeX, which we need to customize by adding a parameter that includes how many columns to include. When we're adding our data to the table each ampersand (&) is a cell separator and a double-backslash (\\) denotes the end of a row.

```latex
\begin{tabular}{ c c c }
cell 1a & cell 1b & cell 1c \\
cell 2a & cell 2b & cell 2c
\end{tabular}

```

We can add some borders to the table using pipes (|) in between our column parameters and horizontal lines with `\hline` rules between the row content. 

```latex
\begin{tabular}{| c | c | c |}
\hline \hline
cell 1a & cell 1b & cell 1c \\
\hline
cell 2a & cell 2b & cell 2c \\
\hline \hline
\end{tabular}
```
We can also add labels and and captions using the `\label` and `\caption` commands, but for those to display correctly we will also want to add a floatable table environment. The h! parameter for the table environment overrides LaTeX table defaults and places the table 'here' in the text of your document.


```latex
\begin{table}[h!]
\centering

\begin{tabular}{| c | c | c |}
\hline \hline
cell 1a & cell 1b & cell 1c \\
\hline
cell 2a & cell 2b & cell 2c \\
\hline \hline
\end{tabular}

\caption{This table is highly scientific.}
\label{table:1}
\end{table}
```
Overleaf provides a more in-depth (introduction to tables LaTeX)[https://www.overleaf.com/learn/latex/Tables#Creating_a_simple_table_in_LaTeX]. 

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
