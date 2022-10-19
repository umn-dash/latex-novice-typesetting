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
- [.to_latex()](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.to_latex.html) in pandas/Python
- [stargazer for R](https://cran.r-project.org/web/packages/stargazer/vignettes/stargazer.pdf)
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

Add borders to the table using pipes (|) in between your column parameters and horizontal lines with `\hline` rules between the row content. 

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
Overleaf provides a more in-depth [introduction to tables LaTeX](https://www.overleaf.com/learn/latex/Tables#Creating_a_simple_table_in_LaTeX). 

## Columns

It's relatively easy to create a two column LaTeX document, by adding a `twocolumn` parameter to your document class statement. 

```latex
\documentclass[twocolumn]{article}
```

To work with more than two columns at a time, you can import the `multicol` package and use the `multicols` environment within your document. In curly brackets following the multicols environment \begin command you can enter the number of columns, and in square brackets you can add any column headers you want to include in between square brackets.

```latex
\usepackage{multicol}
\documentclass{article}

\begin{multicols}{3}
[
\section{Methodology}
]
\lipsum

\end{multicols}

```

We can add a `\setlength` command in the document preamble passing the `\columnsep` parameter with the amount of separation we'd like to see between the columns below. Here's a list of lengths and units you can use in LaTeX. 

```latex
\setlength{\columnsep}{.75cm}

```

OverLeaf's [introduction to Multiple Columns](https://www.overleaf.com/learn/latex/Multiple_columns) goes into greater depth on the many ways to set up different column options in your document. 

## LaTeX templates

Many publishers share document templates for authors in various formats such as Word and, increasingly in the sciences, LaTeX. A great way to learn more about LaTeX is to actually import a LaTeX template in Overleaf and notice the packages and formatting that is built in to the document. 

IEEE, for example, [provides detailed instructions](https://mirrors.concertpass.com/tex-archive/macros/latex/contrib/IEEEtran/IEEEtran_HOWTO.pdf) on how to use the IEEEtran LaTeX class to produce conference and journal submissions to IEEE. 

Let's use the [IEEE Template Selector](https://template-selector.ieee.org) to choose a LaTeX template for a specific journal.

1. Choose Transactions, Journals, and Letters
2. Select the first publication from the list, Canadian Journal of Electrical and Computer Engineering.
3. Choose Original Research and Brief
4. Select the LaTeX file format, and Download the template. 
5. Unzip the folder, and upload the `bare_jrnl_new_sample4.tex` file into Overleaf. 
7. Select the file in Overleaf and choose the Recompile button to view the conference paper template. 

If you scroll through the compiled document you'll see many examples of formatted equations, tables, bullet lists, and much more. You can use the `File outline` in the bottom left corner of Overleaf to jump to different sections of the LaTeX document to see how different content in marked up to follow the IEEE journal style. 

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
