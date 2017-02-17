# Latex Workshop Notes

These notes detail the process we will be going through in order to write and compile incrementally more complex LaTeX documents during the workshop.

Pause between each numbered section to ensure that everyone is caught up. Try to take a break at the 1 hour mark.

## Useful Links

* General Purpose
    * [TexZilla](https://fred-wang.github.io/TeXZilla/): A REPL for Math expressions
    * [Detexify](http://detexify.kirelabs.org/classify.html): Find commands for unknown symbols.
    * [Equation Editor](https://www.codecogs.com/latex/eqneditor.php) GUI for generating code for more complicated expressions
    * [Table Generator](http://www.tablesgenerator.com/): GUI for designing tables that generates copy-pastable source code
    * [CTAN](https://www.ctan.org/pkg): Hosts Latex packages, descriptions, and downloads.
* For installing/using Latex on your local machine:
    * [MikTeX](https://miktex.org/): A Latex "distribution", includes compiler and some packages
    * [Texmaker](http://www.xm1math.net/texmaker/): A Latex IDE
* [Online Markdown Editor](https://jbt.github.io/markdown-editor): The markdown editor used for this document

## Preliminaries
- Create an account on [Sharelatex.com](https://www.sharelatex.com/) and log in to Projects page
- Navigate to the Github Repository: [Repository Link](https://github.com/UCSD-SUMS/latex-w17-workshop)


# 0: Motivation
- What is Latex?
  - A markup language, like HTML, that is aimed at producing printable documents (instead of documents displayed in a browser)
  - Replaces tools like word processors (e.g. Microsoft Word), presentation software (e.g. Keynote/Powerpoint)
- Why Latex instead of something else?
  - Puts **highly professional** typesetting capabilities into your hands
  - Useful for normal documents, but can produce documents that are **publication quality**
  - Easily able to find and use templates made by others
  - The de facto standard for scientific and mathematical documents, esp. journals and conference proceedings
  - Much more logical! You code up the **structure** of your document, so you spend more time focusing on the **content** rather than the formatting or presentation of the final product.
  - [Plus it looks way better :) ]
- But what can you *do* with Latex?
  - View simple PDF Demos:
    - article.pdf
    - beamer.pdf
    - IEEEtran.pdf
  - More intricate examples: [Overleaf Gallery](https://www.overleaf.com/gallery)

------
# 1: Getting a Document to Compile


## Overview
From blank document, add:
```latex
\documentclass{article}
\begin{document}

Document content goes here!

We can't just say y = mx + b.

Use inline math with $y = mx + b$.

Equation math is $$y = mx + b$$

\end{document}
```

## Talking Points
- Project Setup:
  - Create a **New Project**, and select **Blank Project**
    - Name it "Main Document" or something similar
- Optional: If you'd like, have the "skeleton code" in another tab to use as a reference
  - Link: [Skeleton Code](https://www.sharelatex.com/project/58a4f2f837a700427c656307)
  - (Should also be linked in the Github repo's readme
-----
- What is a Latex file? What is a compiler?
- **Three essential lines:**
   - `\documentclass{blah}` (We'll use "article" for our blah)
   - `\begin{document}`
   - `\end{document}`
- What is a command?
   - General form: `\commandName[option1=something, option2=something]{Arguments or text}`
- We'll be saving and compiling often, so it's useful to know the keyboard shortcuts:
   - Ctrl-S to save, Ctrl-Enter to recompile. **Try it now!**
- Okay, it compiled, but produces an empty document!
   - **Add some content between the begin/end sections and compile.**
   - Generally, typing plain text outside of a command is interpreted as actual textual content that should show up in the document.
   - Notice that page numbers are automatically inserted.
   - This is the first instance of an *environment*.
- What is an *environment*?
   - Commands that come in pairs, usually of the form `\begin{someEnvironment}` and `\end{someEnvironment}`
   - Anything occuring between the pairs is considered to be *within* that environment
   - Environments can be nested (we'll see later).
- What about the math??
   - Try typing in a mathematical statement in text mode
      - Same syntax as something like WolframAlpha
      - It doesn't look great.
   - We need to tell the compiler when to expect math instead of text
   - Generally use dollars signs ($) to do this
   - Math Mode vs. Text Mode
      - Typing $ enters inline math mode, then typing $ again exits it.
      - Try typing in $y = mx + b$ and compile
      - Try instead $y = mx$ + b to see the difference
      - Try using block-level math with $$y = mx + b$$
      - **Show that $Typing in math mode$ doesn't work**
- What about applying special formatting to your text?
   - Demonstrate `\textbf{}, \textit{}, \underline{}` environments on sample text content

------
# 2: Work Up to the Sharelatex Default
## Overview
To current document, add:
```latex
\title{My First Document}
\author{D. Zack G.}
\date{February 2017}

... (In document environment)

\maketitle
\section{Introduction}
Document content goes here!
\end{document}
```
## Talking Points

- What is the preamble? What happens there?
  - Insert first several commands and compile
    - Note: these commands don't display anything, they just set variables
    - Insert `\maketitle` inside the document environment **and compile**.
      - Now the title shows up; this command actually handled *rendering* something
    - General pattern: preamble commands mostly set things up, commands within the actual document are the ones that produce visual output
- Structuring your document
  - The article class comes with some commands to help you structure your document
  - We'll look at one: insert `\section{Introduction}` into the document
    - Put this **after** `mktitle` but **before** your actual text and **compile**.
    - Observing results - puts in a nice title, and now we have a numbered section
    - We'll come back to how to further structure your document in a bit
- Slight Break: Let's look at the Sharelatex default template
  - Ctrl-click the Up arrow in the top-left of the screen to open your projects in a new tab
  - There click **New Project** and **Blank Project**
  - Give it a name, then it opens and compiles automatically
  - Most of this code should look familiar - it's what we just wrote! (With one slight addition) 
    -  The addition: `\usepackage[utf8]{inputenc}`, for unicode support
    -  What are packages?
       - Like a programming library, provides extra functionality, new styling or symbols, new commands, etc
       - Sometimes packages come with a Latex distribution, others must be downloaded manually (this can be an involved process!!)
         - Luckily, Sharelatex provides a large number of packages for us behind the scenes, so we don't have to worry for now
       - You can see what's available at the [CTAN](https://www.ctan.org/pkg) website
       - We'll add a few packages of our own later on

------
# 3: Back to Improving Our Document

## Overview
To the existing code, add:
```latex
\title{A \LaTeX Workshop \\ for All Skill Levels}
...
\newpage
\maketitle
...
\section{Content}
	\subsection{Mathematics}
        \subsubsection{Inline Math}
        	Example: $f(x)=ax^2 + c_1$
        \subsubsection{Block-Level Math}
        	Example: $$ \sum_{i=0}^\infty i = -\frac{1}{12} $$
\section{Wrap Up}
	More unrelated text
```

## Talking Points

- Document Classes
- Formatting Commands
  - Line breaks
    - Insert manual line break into title
  - New page
    - Insert newpage just before `\maketitle`
- Subsections
  - Insert sections and subsections (with no content) to see how numbering works
  - Insert content into subsections:
    - Move the math we previously typed in into the appropriate subsections, then compile
  - Insert content into "Wrap Up" section
    - Note that we don't have to close or end the structural commands like section, subsection, etc  
- Math symbols
  - Change inline math section to more complicated quadratic
    - Demonstrates subscript and superscript
  - Change block-level math to sum
    - Uses sub/super script, introduces sum/frac commands which take two arguments
  - Okay, but what about more complicated symbols?
    - Rather than telling you all of the symbols, I'll provide some representatives from each kind of "class" or type of symbol. (Similar symbols have similar syntax!)
    - Demo [TexZilla](https://fred-wang.github.io/TeXZilla/) in Firefox
      - Show several greek letters and equations
      - Show capitalizing greek letters to get capitals
      - Copy/paste `\sum` from earlier into it
      - Show \lim operator
      - Show swapping `\sum` for `\int`
      - Show operators: `sqrt, sin, cos`
      - Show using `\text` for unknown functions
      - Show building derivative out of `\frac`, and `\partial`
      - Show basic array/matrix and how alignment symbol/newline works
      - Show QED
        - Demo [Detexify](http://detexify.kirelabs.org/classify.html)
          - Show searching for other greek letters and operators
        - Demo [Equation Editor](https://www.codecogs.com/latex/eqneditor.php)
          - This is also particular good for when you know what a symbol *looks* like, but not what it's called. 
        - And remember, Google is your friend!!

## Math Examples
```latex
\lim_{n\rightarrow\infty}f(x_n) = f(x)
\sum_{i=0}^\infty i = -\frac{1}{12}
A = \left( \begin{array}{cc} a & b \\ b & c \end{array} \right)
\Box, \blacksquare (From amssym package)
```

------
# 4: Stepping Up the Complexity: References

## Overview

Most of this code should be copy-pasted in to save time, since these topics are relatively easy to Google at any time. (But it is good to see how they work at least onc .)

Add:
```latex
\usepackage{hyperref}
\usepackage{amsmath, amssymb, amsthm}
\usepackage{graphicx}
\usepackage{parskip}
...

\begin{document}
\maketitle
\newpage
\tableofcontents
\newpage
...

\begin{equation} \label{eu_eqn}
e^{\pi i} + 1 = 0
\end{equation}
See Equation~\ref{eu_eqn} 

\begin{equation*}
	\boxed{e^{\pi i} + 1 = 0}
\end{equation*}
...

 Some text.\footnote{\label{myFootnoteName}I'm at the bottom.} More text.
 See footnote~\ref{myFootnoteName}
 ...
 
 For example, see \cite{sourceName2} for more information.

 \begin{thebibliography}{1}
  \bibitem{sourceName1} Amazing Source #1: www.source1.com
  \bibitem{sourceName2} Amazing Source #2: www.source2.com
\end{thebibliography}
```

## Talking Points
- Using packages: Here are some immediately useful ones
  - AMS Stuff
    - Tons of great packages provided by the American Mathematical Society.
    - Quick explanation: This package is meant to solve many small display issues in texts with a lot of mathematical notation, notably with multi-line equations. 
    - Almost always worth including! 
  - hyperref
    - Allows web URLs to be turned into actual, clickable links in the final PDF
    - Very handy for references! 
  - graphicx
    - Handles many of the "fiddly bits" of working with external images (like jpg, png, etc) and makes including them a lot easier.
    - Notably, you don't have to worry about what file type your image is!
  - parskip 
    - Takes out the default indentation that occurs at the beginning of paragraphs. 
    - Useful if you're doing something like a homework assignment or report (as opposed to lengthy exposition)
    
- Table of Contents
  - Remember how we told Latex about the structure of our document using `section`, `subsection`, and so on? Well now it pays off!
  - This command automatically generates a nice table of contents wherever it is called.
  - **Insert the `\tableofcontents` code into your document**
  - Also, since we used the `hyperref` package, the section titles are **clickable links**!
  
- The Equation Environment, labels, and back-references
  - The equation environment (with the help of some tweaks from the AMS math package) is the definitive way to display big, important results or formulas
  - The effect is similar to what we did with the \$\$ environment, with a few bonus features - equation numbering, for one, but also better spacing and text flow
  - And since equations are numbered, we can reference them later *extremely* easily.
  - **Insert the `\begin{equation}` code now** 
  - Note: on some Latex distributions, you may need to compile *twice* to get references to work
  - **Demonstrate `equation*`**
  - **Demonstrate `\boxed`**
  
- Footnotes
  - A standard feature, but latex lets you write your footnotes right along with your actual content
  - Of course, when it's displayed, it's at the bottom of the page as usual
  - **Insert code for `\footnote`**
  - You can also reference them just like equations
  - **Insert code for `\ref`**
  
- Bibliography
  - Another standard feature - you define it in its own environment at the end of the document, add entries and give them custom labels/names, then you can reference it anywhere else by that custom name
  - **Insert `\begin{bibliography}, \bibitem{}` and compile**
  - **Demonstrate `\cite` command**
  - There are many tools for managing bilbiographies through Latex - the most popular one is Bibtex
    - There is a bit of a learning curve to this tool, usually only worth diving into it for books, research projects, theses, or lecture notes with *many* references 
    - Most journals available online export Bibtex-compatible files, which you can just put in a directory and have our bibliography auto-populated

Save this document as your template!

------
# 5: Graphics: 
Do this in a new project! Copy-paste most things to emphasize that some of these are worth saving as snippets, instead of remembering every detail.

## Overview

**main.tex**
```latex
\usepackage{graphicx}
...

\section{Introduction}
\begin{figure}[]
    \centering
    \includegraphics[width=4cm]{image1}
    \label{fig:img1}
    \caption{Homotopy groups of spheres}
\end{figure}

\begin{align}
  f(x) &= (x+a)(x+b) \\
  &= x^2 + (a+b)x + ab
\end{align}
```


## Talking Points

- We've built a pretty fully-featured document so far. But since these last few bits are slightly more complex, we'll do it in a new project.
- Setting up the new project:
  - **Start a new blank project**
  - Search Google for an image (png or jpg preferably), download it, then upload it into your project
  	- I chose the term "homotopy" and got 
![Image of Yaktocat](https://upload.wikimedia.org/wikipedia/commons/thumb/6/67/Homotopy_of_pointed_circle_maps.png/220px-Homotopy_of_pointed_circle_maps.png)
  - Rename the image **"image1.png", "image1.jpg"**, or whatever file type you found.


- The Figure environment
  - *The* way to include images in your documents, but this process can be very fiddly!
  - Most of what we type into Latex is a *suggestion* to the Latex compiler of where things go and how they should be placed.
  - Images can be very complex - differing sizes/shapes, aspect ratios, alignment, how they flow with text...there are many variables to consider
  - So by default, your images *may* not show up exactly where you put them in the text!
  - **Insert figure code, note bad image placement**
  - **Add `h` option to figure to force better placement**
  
- The align and align\* environments
	- **Provided by amsmath**
	- Useful for for showing a series of calculations
	- Also good for making multiline math line up
	- Many other "aligned" environments behave like this one (tables, arrays/matrices, etc)
	- User ampersands to denote 'anchors' where columns should line up\
		- Must have the same number in each row!
	- **Insert align code**
	- **Demonstrate align\***

- The Tikz package
  - A *very* brief overview, so people know it exists
  - Useful CS (graphs, trees), EE (circuits, control systems), Math (commutative diagrams). 
  - Relatively simple, but also very powerful/extensive. Has a learning curve though.
  - **Do not live code, just show diagram.tex after it's compiled**

------
# 6: Managing Large Documents or Projects

Code up the "input" option, but only demonstrate the others - there is too much boilerplate in those to live code.

## Overview

**main.tex**
```latex
\documentclass{article}

\title{This is a workshop}
\author{Zack Garza}

\begin{document}

\maketitle

\section{Lecture 1}
\input{"lecture1.tex"}

\section{Lecture 2}
\input{"lecture2.tex"}

\end{document}
```

**lecture1.tex**
```latex
Notes: $y = mx + b$
```

**lecture2.tex**
```latex
A large equation $$f(x) = a^x$$
```

## Talking Points
- Why use documents and subdocuments?
	- Invaluable for bigger project - e.g. break thesis/dissertation or book into individual chapters or sections
	- Can work on individual parts without breaking the main document (useful when collaborating)
- **Add a blank file: lecture1.tex**
- **Add a blank file: lecture2.tex**
- Setting up directory structure
- 3 major options, in roughly increasing order of complexity
  - Input Command -  **Uses `\input` command**
  	- Easiest! Built in, so no external packages.
  	- Useful when you just want to break your document up into smaller pieces
  	- The smaller pieces are not full latex documents though, and will not compile
  - Subfiles Package - **Uses `\subfile` command**
  	- A little more complex. 
  	- Documents will now compile on their own, but they're not pretty
  		- But you can still check that your syntax is right before including!
  	- Subdocuments must inherit the preamble from the main document
  	- This means if you use extra packages/commands/tweaks in the subdocuments, you have to remember to put them in the main doc to get them to "stick"
  - Standalone Package - **Uses `\import` command**
  	- Most complex.
  	- Best option for big or long-term projects
  	- Best option for modularity and reusability of entire sections
  	- Each subdocument is a **complete document** on it's own, with it's own preamble, packages, commands, everything!
  		- So you can compile the subdocument and know that what you see is almost surely what it will look like in the larger main document
    	- Makes it easy to hone your section until it's perfect, and keeps packages linked with files that actually use them.

- Input Command:
	- **Insert sections and inputs into main.tex**
	- **Insert content into lecture1 and lexture2**
	- **Compile main.tex**
