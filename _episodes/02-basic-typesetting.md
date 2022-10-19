---
title: "Text Formatting"
teaching: 25
exercises: 10
questions:
- "Key question: How can I format text within a LaTeX document?"
- "Key question: How can I use different styles and classes of documents?"
- "Key question: How can I style mathematical equations in LaTeX?"

# Basic typesetting

We are now going to introduce some commands you can use to format your text. Let's continue working with the main.tex file from the previous lesson.

```latex
\documentclass{article}
\usepackage[utf8]{inputenc}
\usepackage{lipsum}

\title{Let's do Science!}
\author{Your Name}

\begin{document}

\maketitle

\section{Abstract}
\lipsum

\section{Introduction}
\lipsum

\end{document}
```

Previously, we inserted some random text using `lipsum`, but because that is 
generated via a command, we couldn't format the text itself. Let's remove the lipsum command from our document and start adding some formattable text instead.  

You might notice that the Abstract is being enumerated (1, 2, 3...) along with the other "sections" of the article, which isn't usually how articles are formatted. In this case, LaTeX provides an environment we can use for our Abstract. Delete the \section{Abstract} command, and create a new Abstract environment instead:

```latex
\begin{abstract}
	The scientific method is really cool. I mean, seriously, it is awesome!
\end{abstract}
``` 

Let's take a look at some of the commands we can use to format text. We can format words or phrases using commands for bold, italics, underline, subscripts, superscripts and more by passing the text we want emphasized as arguments to the command:

```latex
\begin{abstract}
	The \textbf{scientific method} is really cool. I mean, seriously, it is \textit{awesome}! It is the 1\textsuperscript{st} method that you should use when you want to do science. Can you imagine what technology & engineering would look like without the scientific method?
\end{abstract}
```

Notice that the ampersand (&) disappears from the text after you recompile the document! That's because a number of characters are reserved in LaTeX, and if we want to include them in our text we first have to "escape" them with a backslash (\). Some of those special characters are: 
> \# $ % ^ & _ { } ~ \. 

To display the ampersand after compiling our doc, we should add a backslash as an "escape character" before the ampersand:
```latex
\begin{abstract}
	The \textbf{scientific method} is really cool. I mean, seriously, it is \textit{awesome}! It is the 1\textsuperscript{st} method that you should use when you want to do science. Can you imagine what technology \& engineering would look like without the scientific method?
\end{abstract}
```

### Lists

Let's add some of the reasons we love the scientific method to our abstract using the ```{itemize}``` environment:
```latex
\begin{itemize}
	\item It makes it less likely that bridges will collapse.
	\item It helps us to build airplanes so we can fly.
\end{itemize}
```

If we wanted to change it from an unordered list to a numbered/ordered list we could use the ```{enumerate}``` environment instead:
```latex
\begin{enumerate}
   	\item It makes it less likely that bridges will collapse.
	\item It helps us to build airplanes so we can fly.
\end{enumerate}
```

> ## Document classes and sections
Articles are not the only kinds of documents we can create in LaTeX. We could also assign document classes such as:
> * ```\documentclass{minimal}```
* ```\documentclass{report}```
* ```\documentclass{slides}```
* ```\documentclass{letter}```
* ```\documentclass{book}```
> 
> Go ahead and change your document class and recompile to see how the format changes. Some commands, like ```\section```, won't work in every document class. 
{: .callout}

We can also customize the document class using options [] to add styles across the entire document.

```latex
\documentclass[12pt,letter]{article} % use 12 point font on 8.5 x 11 inch (letter) paper
```

The code above also includes a comment - all of the text after the percentage symbol - which will be ignored when the document is compiled. 

### Sections & subsections
We've seen how we can organize an article with \section commands. We can also add different levels of headings and sub-headings. Let's outline some of the pillars of science that we want to touch on in our introduction.

```latex

\section{Introduction}
	
\subsection{Math}

\subsection{Experiments}

\subsection{Scientific Computing}

\subsubsection{Algorithms}

```
> ## Quote marks
> Adding quotations to your text in a LaTeX document can be challenging. Copying quote marks from other documents is likely to create errors, or show up as weird characters in your text. To add left and right quote marks in LaTeX it's best to add two grave accents (to the left of the 1 key) as your left quote mark and two single quotes (to the left of the Return/Enter key) as your right quote:
> ```latex
> \section{Introduction}
> A ``quote'' in a phrase works like this.
> Using "double quotes" will look bad.
> ``To add a `quote' in a quote you should add the double grave and single quotes outside of a single grave and single quote mark.''
> ```
> Add regular quotes to your document and compile to see what they look like. Now try to add the grave accents and single quotes to compare. 
{: .callout}

### Math typesetting
One of the primary advantages to using LaTeX, as opposed to other typesetting software, is its ability to format mathematical equations. 
You can use dollar signs to set apart formulas in your text, or use the ```equation``` environment to create larger displays. In both of the equations below we'll use the carat symbol to add powers/superscripts:

```latex
\subsection{Math}
Einstein discovered $e=mc^2$.

We can also set aside a formula from the text:
\begin{equation}
a^2 + b^2 = c^2
\end{equation}

```
Many of the reserved characters we noted above can be used in LaTeX within the math environments. So these symbols will display correctly when set apart using the dollar signs or ```{equation}``` environment:

```latex
+ - = ! / ( ) [ ] < > | ' : *
```

Some other commonly used characters and tips for equations:
- the carat symbol (^) for powers/superscripts
- underscore for subscripts
- ```\alpha \gamma \delta``` render the greek letters by cased name

It's also quite common to use commands that take values as parameters to present equation symbols. For example ```\sqrt{}``` for displaying square roots, ```\sum{}``` for the sum symbol, and ```\int{}``` for the integral symbol. We can space out the equations a bit by adding line breaks using double backslashes (`\\`).

```latex
$\sqrt{4}$
\\
\\
$\sum{P(i,j)}$
\\
\\
$\int_0^\infty$
```
There are a lot of potential formatting choices to make when building your formulas. Wikipedia's [LaTeX/Mathematics page](https://en.wikibooks.org/wiki/LaTeX/Mathematics) is a good quick reference, while The American Mathematical Society's [Short Math Guide for LaTeX](http://tug.ctan.org/info/short-math-guide/short-math-guide.pdf) goes into a little more detail. 


> ## Challenge 1
>
> Using Wikipedia's quick guide, how would you render the fraction 5/8? 
> 
>
> > ## Answer
> >```latex
> >\frac{5}{8}
> >```
> > {: .tex}
> {: .solution}
{: .challenge}
>
>
> ## Challenge 2
>
> How would you format the square root of a over b?
> ![equation for square root of a over b](https://wikimedia.org/api/rest_v1/media/math/render/svg/aa0aee8692897b7ee635498e8c34d4531da3e346)
>
> > ## Answer
> >```latex
> >\sqrt{\frac{a}{b}}
> >```
> > {: .tex}
> {: .solution}
{: .challenge}
>
>
