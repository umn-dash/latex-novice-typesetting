---
title: "Text Formatting"
teaching: 0
exercises: 0
questions:
- "Key question: "
- "Key question: "
objectives:
- "First learning objective."
- "Second learning objective. "
keypoints:
- "First key point. "
- "Second key point. "
- "Third key point. "
---

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
generated via a command, we couldn't format the text itself. Let's remove the lipsum command from our document and start adding some format-able text instead.  

You might notice that the Abstract is being enumerated (1, 2, 3...) along with the other "sections" of the article, which isn't usually how articles are formatted. In this case, LaTeX provides an environment we can use for our Abstract. Delete the \section{Abstract} command, and create a new Abstract environment instead:

```latex
\begin{abstract}
	The scientific method is really cool. I mean, seriously, it is awesome!
\end{abstract}
``` 

Let's take a look at some of the commands we can use to format text. We can format words or phrases using commands for bold, italics, underline, subscripts, superscripts and more by passing the text we want emphasized as arguments to the command:

```latex
\begin{abstract}
	The \textbf{scientific method} is really cool. I mean, seriously, it is \textit{awesome}! It is the 1\textsuperscript{st} method that you should use when you want to do science.
\end{abstract}
```
We can add another line to our abstract and recompile:
```latex
\begin{abstract}
	The \textbf{scientific method} is really cool. I mean, seriously, it is \textit{awesome}! It is the 1\textsuperscript{st} method that you should use when you want to do science. Can you imagine what technology & engineering would look like without the scientific method?
\end{abstract}
```

Notice that the ampersand (&) disappears from the text after recompiling! That's because a number of characters are reserved in LaTeX, and if we want to include them in our text we first have to "escape" them with a backslash (\). Some of those special characters are: 
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
	\item It makes it less likely for bridges to collapse.
	\item It's helpful for the creation and improvement of airplanes so we can fly to cool places.
\end{itemize}
```

If we wanted to change it from an unordered list to a numbered/ordered list we could use the ```{enumerate}``` environment instead:
```latex
\begin{enumerate}
   	\item It makes it less likely for bridges to collapse.
   	\item It's helpful for the creation and improvement of airplanes so we can fly to cool places
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

### Packages for document styles

You can import packages in your LaTeX document to add functionality beyond the default LaTeX. We added some document styles to the document class above using options, but we could also import the geometry package to further customize the page layout. Import packages before the ```\begin{document}``` command with the ```\usepackage{}``` command. Let's remove the documentclass options for a 12pt font and letter paper and add an option for 1.5 inch margins using geometry.

```latex
\documentclass{article}
\usepackage[margin=1.5in]{geometry}

```
### Sections & subsections
We've seen how we can organize an article with \section commands. We can also add different levels of headings and sub-headings. Let's outline some of the pillars of science that we want to touch on in our introduction.

```latex

\section{Introduction}
	
\subsection{Theory}

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


