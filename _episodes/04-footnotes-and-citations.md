---
title: "Citations and BibTex"
teaching: 0
exercises: 0
questions:
- "Key question: How can I add footnotes and bibliographies to a LaTeX document?"
- "Key question: How can I use BibTeX to organize citations for larger projects?"
objectives:
- "First learning objective. Learn how to place references within the text of a scholarly article."
- "Second learning objective. Learn how to associate references in the text with citations organized in a BibTex file."
- "Third learning objective. Learn how to generate a bibliography from the citations in BibTex."
keypoints:
- "First key point. You can manually add footnotes inline with the text using the `\footnote{}` command."
- "Second key point. BibTeX is a file format that allows you to keep track of citation data separately from your main LaTeX document."
- "Third key point. You can reference citations in a BibTeX file using the `biblatex` package."
- "Fourth key point. You can change the citation style used in `biblatex` by passing the `[style=...]` option."
---

## Footnotes

We can use the `\footnote{}` command, to add citations as footnotes, where the argument will be the text of the footnote. First let's start a Literature Review section (you can delete the lipsum from the Introduction so it's easier to see our lit review). 

```latex

\section{Literature review}
The scientific method was created a long time ago. One person who gets a lot of credit is Galileo Galilee. But others note that the scholar Ibn Al-Haytham developed similar thinking around 1000 CE in Basra and Baghdad. 
```

Now let's add some footnotes to acknowledge our sources, using the `\footnote{}` command:

```latex

\section{Literature review}
The scientific method was created a long time ago. One person who gets a lot of credit is Galileo Galilee\footnote{Finocchiaro, M. (2012). \textit{Galileo and the Art of Reasoning: Rhetorical Foundation of Logic and Scientific Method.} Springer}. But others note that the scholar Ibn Al-Haytham developed similar thinking around 1000 CE in Basra and Baghdad\footnote{Gorini R. Al-Haytham the man of experience: First Steps in the Science of Vision. \textit{J Inter Soc for the History of Islamic Medicine (JISHIM)} 2003;2(4):53–55.}. 
```

## BibTeX
You can manually add citations and footnotes in this manner but you can see that the citation styles above don't match. Rather than trying to format each citation on our own, we can use a tool and file format called BibTeX to format our citations and footnotes consistently across a scholarly work. 

There are a number of different ways to use BibTeX on Overleaf. We'll use the 'biblatex' package. First, you'll want to add your references to a .bib (plain-text) file in the [BibTex file format](http://www.bibtex.org/Format/). Then we'll import the ```biblatex``` package and use its ```\addbibresource{}``` command to refer to our .bib file. You can often generate citations in BibTex format directly from scholarly databases or you can export them from citation managers like Zotero or Mendeley. Let's download the [refs.bib file](../data/refs.bib) with the citations from above in the proper BibTex format, and upload the file to Overleaf.

![The upload button in Overleaf is located above the file navigator and has a disk icon with an up arrow](../fig/overleaf_upload.png)

You should now see a refs.bib file and main.tex in your file navigator in Overleaf. Open the refs.bib file and take a look at the contents. 

To use these references in your LaTeX document you can import the biblatex package and also refer to the name of the refs.bib file with the ```\addbibresource{}``` command. Add the following to the header of the main.tex file:
```latex
\usepackage{biblatex} 
\addbibresource{refs.bib}
```

Then we can replace the footnotes with the ```\cite{}``` command using the citation-key for each reference as the cite command's argument. The citation-key is the first item in the curly brackets following a BibTex entry. For example, 'tbackhi_ibn_2007' is the citation-key in the ```@article{tbakhi_ibn_2007,``` reference. You can change the citation-keys to be anything you want, but usually they consist of the author's name and year. 
```latex
\section{Literature review}
The scientific method was created a long time ago. One person who gets a lot of credit is Galileo Galilee \cite{finocchiaro_galileo_1980}. But others note that the scholar Ibn Al-Haytham developed similar thinking around 1000 CE in Basra and Baghdad \cite{tbakhi_ibn_2007}.
```

You'll notice that the numbered citation footnotes show up in the text, but the references don't appear as footnotes at the bottom of the page anymore. To add our list of references, we can add the command ```\printbibliography``` at the end of the document:

```latex
\printbibliography
\end{document}
```

If you want the Bibliography to follow a specific citation style there are a variety of [styles](https://www.overleaf.com/learn/latex/Biblatex_citation_styles#Citation_styles) you can pass as an option - ```[style=...]``` - of the ```\usepackage{biblatex}``` package. If you are submitting your paper for an IEEE publication, for example, you can add the following to the head of your document

```latex
\usepackage[style=ieee]{biblatex} 
```

> ## Challenge 1
>
> Can you change the style of your citations to use Chicago's Author/Date formatting? It should look something like the examples below. 
> 
> Note: do you have to add any other characters to the ```\cite{}``` commands in your text to make those citations appear correctly (with parentheses)?
> ![The scientific method was created a long time ago. One person who gets a lot of credit is
Galileo Galilee (Finocchiaro). But others note that the scholar Ibn Al-Haytham developed
similar thinking around 1000 CE in Basra and Baghdad (Tbakhi and Amr).
References
Finocchiaro, M. A. Galileo and the Art of Reasoning: Rhetorical Foundation of Logic and
Scientific Method [inlangen]. Springer Science & Business Media, Dec. 1980. isbn: 978-
94-009-9017-3.
Tbakhi, Abdelghani, and Samir S. Amr. “Ibn Al-Haytham: Father of Modern Optics”. An-
nals of Saudi Medicine 27, no. 6 (2007): 464–467. issn: 0256-4947, visited on 08/23/2022.
https://doi.org/10.5144/0256-4947.2007.464. https://www.ncbi.nlm.nih.gov/
pmc/articles/PMC6074172/.
1
](../fig/overleaf_chicago.png)
>
> > ## Answer
> >
> > Add the ```chicago-authordate``` style to your ```\usepackage``` options, and add parentheses around the ```\cite{}``` commands in your text:
> >  ```latex
> > \usepackage[style=chicago-authordate]{biblatex} 
> > ...
> > The scientific method was created a long time ago. One person who gets a lot of credit is Galileo Galilee (\cite{finocchiaro_galileo_1980}). But others note that the scholar Ibn Al-Haytham developed similar thinking around 1000 CE in Basra and Baghdad (\cite{tbakhi_ibn_2007}).
> > ``` 
> >
> > {: .tex}
> {: .solution}
{: .challenge}
>
>
