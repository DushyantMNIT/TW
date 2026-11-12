# LaTeX Technical Documentation & Reference Guide

A comprehensive, example-driven reference guide for **LaTeX typesetting**, structured as a modular documentation page for Technical Writing coursework. This guide synthesizes core concepts from introductory document setup to advanced mathematical environments, custom tables, figure management, color formatting, and native vector graphics using the LaTeX `picture` environment.

---

## 1. Document Structure & Fundamental Mechanics

LaTeX is a document preparation system that separates content from visual styling. Plain text source files (`.tex`) are compiled into publication-ready PDF, DVI, or PostScript outputs.

### 1.1 Essential Document Anatomy
Every valid LaTeX document requires a document class definition and a `document` environment:

```latex
\documentclass[12pt, a4paper]{article}

% Preamble: Package imports and global settings
\title{Technical Writing & Typesetting Guide}
\author{Prof. Neeta Nain \and Student Contributor}
\date{\today}

\begin{document}

\maketitle

\begin{abstract}
This document outlines the core technical mechanics of LaTeX typesetting, including structured sectioning, mathematical derivation typesetting, complex tables, graphics inclusion, and coordinate-based drawing.
\end{abstract}

\section{Introduction}
LaTeX automates layout configuration, section numbering, cross-referencing, and bibliography generation.

\end{document}
```

### 1.2 Document Classes Overview
The `\documentclass[options]{class}` directive sets global page layout rules and formatting defaults.

| Class | Primary Purpose | Structural Features |
| :--- | :--- | :--- |
| `article` | Short papers, lab reports, homework | Uses `\section`, `\subsection`; no `\chapter` support |
| `report` | Longer technical reports, dissertations | Supports `\chapter`, front matter, separate title page |
| `book` | Textbooks, manuals, monographs | Supports `\frontmatter`, `\mainmatter`, `\backmatter`, chapters |
| `beamer` | Slide presentations | Frame-based slide structure with overlays and themes |
| `letter` | Formal correspondence | Custom opening, closing, address, and signature blocks |
| `exam` | Tests and quizzes | Includes `questions`, `choices`, and `solution` environments |

### 1.3 Sectioning, Spacing, and Reserved Characters
- **Hierarchy Commands**: `\section{...}`, `\subsection{...}`, `\subsubsection{...}`, `\paragraph{...}`
- **Paragraphs & Spacing**: A blank line in the source file begins a new paragraph. Use `\vspace{10mm}` for explicit vertical spacing and `\noindent` to suppress paragraph indentation.
- **Line Breaks**: Use `\\` for manual line breaks within a paragraph without starting a new paragraph. Use `\newpage` or `\clearpage` to force page breaks.
- **Reserved Characters**: The following ten characters have special syntax meanings and must be escaped with a backslash when typed as literal text:
  - Escaped: `\$`, `\&`, `\%`, `\#`, `\_`, `\{`, `\}`
  - Special commands: `\textasciitilde` (`~`), `\textasciicircum` (`^`), `\textbackslash` (`\`)
- **Page Styles**: Controlled via `\pagestyle{style}`:
  - `plain`: Default; prints page numbers at the bottom center.
  - `headings`: Displays section headers and page numbers in the top header.
  - `empty`: Suppresses all headers and footers.

---

## 2. Mathematical Typesetting

LaTeX provides robust native tools and `amsmath` extensions for inline and display mathematics.

### 2.1 Inline vs. Display Math Mode
- **Inline Math**: Enclosed in `$ ... $` or `\( ... \)`. Fits within standard text lines without altering line height (e.g., $A = \pi r^2$).
- **Display Math**: Enclosed in `\[ ... \]` or `\begin{equation} ... \end{equation}`. Centers the formula on its own line and assigns automated equation numbers when using the `equation` environment.

```latex
% Inline Math
The energy-mass equivalence is expressed as $E = mc^2$.

% Unnumbered Display Math
\[
\int_{0}^{1} x^2 \, dx = \frac{1}{3}
\]

% Numbered Display Math
\begin{equation}
\sum_{i=1}^{n} i = \frac{n(n+1)}{2}
\label{eq:gauss_sum}
\end{equation}
```

### 2.2 Symbols, Operators, and Notations
- **Fractions & Roots**: `\frac{numerator}{denominator}`, `\sqrt{x}`, `\sqrt[n]{y}`
- **Subscripts & Superscripts**: `x_{i}^{2}`, `e^{-x}`
- **Summations & Integrals**: `\sum_{k=1}^{m} k`, `\int_{a}^{b} f(x)\,dx`, `\prod_{i=1}^{n} x_i`
- **Relational & Logic Symbols**: `\leq` ($\leq$), `\geq` ($\geq$), `\neq` ($\neq$), `\approx` ($\approx$), `\infty` ($\infty$), `\cap` ($\cap$), `\cup` ($\cup$), `\subseteq` ($\subseteq$)
- **Greek Letters**: `\alpha`, `\beta`, `\gamma`, `\delta`, `\pi`, `\theta`, `\lambda`
- **Overbrace & Underbrace**:
  ```latex
  \[
  \overbrace{a + b + c}^{d} \quad \underbrace{a + b + c}_{d}
  \]
  ```

### 2.3 Arrays, Piecewise Functions, and Matrices
Matrix and array structures require the `amsmath` package.

```latex
% Aligned Array Table inside Math Mode
\[
\begin{array}{lcr}
\text{Left} & \text{Center} & \text{Right} \\
a & b & c \\
1 & 2 & 3
\end{array}
\]

% Piecewise Function using Array & Automated Delimiters
\[
f(x) = \left\{
\begin{array}{ll}
-x, & x < 0 \\
0, & x = 0 \\
x^2, & x > 0
\end{array}
\right.
\]

% Matrix Variants
\[
\begin{matrix} 1 & 2 \\ 3 & 4 \end{matrix} \quad        % Plain matrix
\begin{pmatrix} 1 & 2 \\ 3 & 4 \end{pmatrix} \quad       % Parentheses ()
\begin{bmatrix} a & b \\ c & d \end{bmatrix} \quad       % Square brackets []
\begin{vmatrix} x & y \\ z & w \end{vmatrix}             % Determinant | |
\]

% Small Inline Matrix
$ \left( \begin{smallmatrix} a & b \\ c & d \end{smallmatrix} \right) $
```

---

## 3. Formatting Tables (`tabular` & `table`)

Tables organize structured data using columns separated by `&` and rows terminated with `\\`.

### 3.1 Basic `tabular` Environment
Column alignment specifiers: `l` (left), `c` (center), `r` (right), `p{width}` (fixed width wrapped column), `|` (vertical border line).

```latex
\begin{tabular}{|c|c|r|}
\hline
\textbf{Item} & \textbf{Quantity} & \textbf{Price (\$)} \\
\hline
Notebook & 10 & 25.00 \\
Pen & 50 & 15.50 \\
\hline
\end{tabular}
```

### 3.2 Floating `table` Environment, Captions, and Styling
Wrapping `tabular` inside `table` adds floating placement control, captions, labels, and customizable dimensions.

```latex
\usepackage{multirow} % Required for \multirow

\begin{table}[h!]
\centering
\renewcommand{\arraystretch}{1.5}    % Row height factor
\setlength{\tabcolsep}{12pt}         % Column spacing
\setlength{\arrayrulewidth}{0.4mm}   % Border thickness

\begin{tabular}{||l|c|r||}
\hline\hline
\textbf{Category} & \textbf{Sub-item} & \textbf{Score} \\
\hline\hline
\multirow{2}{*}{Hardware} & CPU & 95 \\
                          & RAM & 88 \\
\hline
Software & OS & 92 \\
\hline\hline
\end{tabular}
\caption{System Evaluation Matrix}
\label{tab:system_eval}
\end{table}
```

- **Placement Parameters**: `h` (here), `t` (top), `b` (bottom), `p` (page of floats), `!` (override default limits).

---

## 4. Figures and Graphics (`graphicx`)

Including external image files (PNG, JPG, PDF, EPS) requires loading `\usepackage{graphicx}` in the document preamble.

### 4.1 Basic Image Import & Manipulation
```latex
% Scaling by percentage of text width
\includegraphics[width=0.5\textwidth]{diagram.png}

% Explicit dimensions, rotation, and cropping
\includegraphics[width=4cm, height=3cm, angle=45]{plot.pdf}
\includegraphics[trim=10 20 10 20, clip, width=5cm]{figure.png}
```

### 4.2 Floating Figures & Side-by-Side Layouts

```latex
% Single Centered Floating Figure
\begin{figure}[h!]
\centering
\includegraphics[width=0.6\textwidth]{architecture.png}
\caption{System Architecture Overview}
\label{fig:arch}
\end{figure}

% Side-by-Side Images using minipage
\begin{figure}[h!]
\centering
\begin{minipage}{0.45\textwidth}
  \centering
  \includegraphics[width=\linewidth]{chart_a.png}
  \caption{Primary Model Performance}
  \label{fig:chart_a}
\end{minipage}
\hfill
\begin{minipage}{0.45\textwidth}
  \centering
  \includegraphics[width=\linewidth]{chart_b.png}
  \caption{Baseline Comparison}
  \label{fig:chart_b}
\end{minipage}
\end{figure}
```

---

## 5. Colors & Custom Highlighting (`xcolor`)

Visual styling, colored text, background highlighting, and frame boxes are managed via `\usepackage{xcolor}`.

```latex
\usepackage{xcolor}

% Defining custom colors
\definecolor{myblue}{RGB}{10, 60, 200}
\definecolor{softpink}{HTML}{FFB6C1}
\definecolor{alertred}{named}{red!80!black}

% Text Color Applications
\textcolor{red}{Standard Red Text}
\textcolor{myblue}{Custom RGB Blue Text}

% Scope-based color change
{\color{alertred} This block is Alert Red}, while surrounding text returns to normal.

% Background Highlights and Box Outlines
\colorbox{yellow}{Important Highlighted Text}
\fcolorbox{red}{white}{Critical Alert Label}
```

---

## 6. LaTeX `picture` Environment (Vector Graphics)

The native LaTeX `picture` environment allows technical writers to draw diagrams, coordinate axes, schematics, and geometric illustrations directly in code without external graphic tools.

### 6.1 Canvas Setup & Coordinate Mechanics
The canvas size is set in units defined by `\unitlength`. Coordinates $(x,y)$ position objects relative to an origin (default: lower-left corner).

```latex
\setlength{\unitlength}{1cm} % Set unit length to 1 centimeter

\begin{picture}(width, height)(x-offset, y-offset)
    \put(x, y){object}
\end{picture}
```

### 6.2 Primary Drawing Commands & Syntax

| Command | Arguments | Description & Rules |
| :--- | :--- | :--- |
| `\unitlength` | Length parameter | Sets global unit scaling (e.g., `1cm`, `0.5in`, `10pt`). Default is `1pt`. |
| `\put(x,y){obj}` | Coordinates $(x,y)$, object | Places `obj` at $(x,y)$. Lower-left corner of text boxes serves as reference point. |
| `\line(dx,dy){length}` | Slope integers $(dx,dy)$, horizontal length | Draws a line. Slopes $(dx,dy)$ must be integers between $-6$ and $6$ with no common factors. |
| `\vector(dx,dy){length}`| Slope integers $(dx,dy)$, horizontal length | Draws an arrow. Slopes $(dx,dy)$ must be integers between $-4$ and $4$. |
| `\circle{diameter}` | Circle diameter | Draws an open circle centered at the `\put` coordinates. |
| `\circle*{diameter}` | Disk diameter | Draws a solid filled circle (disk) centered at the coordinates. |
| `\oval(w,h)[portion]` | Width $w$, height $h$, optional portion (`t`,`b`,`l`,`r`)| Draws a rectangle with rounded corners. |
| `\framebox(w,h)[pos]{text}`| Dimensions $(w,h)$, alignment (`c`,`t`,`b`,`l`,`r`), text | Draws a framed box of size $w \times h$ containing text. |
| `\makebox(w,h)[pos]{text}` | Dimensions $(w,h)$, alignment, text | Places unframed text aligned within a region of size $w \times h$. |
| `\dashbox{dash_len}(w,h){text}` | Dash length, dimensions, text | Draws a dashed frame around text. Box size should be multiples of `dash_len`. |
| `\multiput(x,y)(dx,dy){n}{obj}` | Initial $(x,y)$, step $(dx,dy)$, count $n$, object | Repeatedly draws $n$ copies of `obj` spaced by step displacement $(dx,dy)$. |
| `\shortstack[pos]{line1 \\ line2}` | Alignment (`l`,`c`,`r`), multiline text | Creates a compact vertical stack of text items. |
| `\linethickness{dim}` | Dimension (e.g., `1pt`, `0.5mm`) | Sets thickness for horizontal/vertical lines and frames. |

### 6.3 Complete Drawing Examples

#### Example A: Coordinate Axes with Vectors and Circle
```latex
\setlength{\unitlength}{1cm}
\begin{picture}(6, 4)(0, 0)
    % Draw X and Y Axes with vectors
    \put(0, 0){\vector(1, 0){5}} % X-axis arrow pointing right
    \put(0, 0){\vector(0, 1){3}} % Y-axis arrow pointing up
    
    % Axis Labels
    \put(5.1, 0){\makebox(0,0)[l]{$x$}}
    \put(0, 3.2){\makebox(0,0)[c]{$y$}}
    
    % Circle at coordinate (3, 2)
    \put(3, 2){\circle{0.6}}
    \put(3, 2){\circle*{0.1}} % Center point
    \put(3.2, 2.2){\makebox(0,0)[l]{$P(3,2)$}}
\end{picture}
```

#### Example B: LNL Block Diagram System
```latex
\begin{figure}[h!]
\centering
\setlength{\unitlength}{0.14in}
\begin{picture}(32, 12)
    % Block Boxes
    \put(3, 4){\framebox(6, 3){$H_B(q)$}}
    \put(13, 4){\framebox(6, 3){$N[\cdot]$}}
    \put(23, 4){\framebox(6, 3){$H_C(q)$}}
    
    % Connecting Interconnect Vectors
    \put(0, 5.5){\vector(1, 0){3}}
    \put(9, 5.5){\vector(1, 0){4}}
    \put(19, 5.5){\vector(1, 0){4}}
    \put(29, 5.5){\vector(1, 0){3}}
    
    % Signal Labels
    \put(-1, 6.5){$u(k)$}
    \put(9.5, 6.5){$x_B(k)$}
    \put(19.5, 6.5){$x_C(k)$}
    \put(30, 6.5){$y(k)$}
\end{picture}
\caption{LNL Block-Oriented System Model}
\label{fig:lnl_block}
\end{figure}
```

#### Example C: Array of Repeated Elements using `multiput`
```latex
\setlength{\unitlength}{0.8cm}
\begin{picture}(8, 2)
    % Draw 6 solid dots spaced 1 unit apart horizontally
    \multiput(1, 1)(1, 0){6}{\circle*{0.25}}
    
    % Connect first and last dot with a dashed box
    \put(0.5, 0.5){\dashbox{0.2}(6, 1)[c]{Dot Array}}
\end{picture}
```

---

## 7. Troubleshooting & Compilation Workflow

### 7.1 Compilation Tools
- **PDFLaTeX Workflow**: Compiles directly from source to PDF.
  ```bash
  pdflatex document.tex
  ```
- **BibTeX Bibliography Resolution**: Requires a 4-step compilation sequence to link references.
  ```bash
  pdflatex document.tex
  bibtex document
  pdflatex document.tex
  pdflatex document.tex
  ```

### 7.2 Common LaTeX Errors and Solutions
1. **`Bad \line or \vector argument`**: Slopes $(dx,dy)$ exceed integer limits (greater than 6 for lines, 4 for vectors) or share common factors.
2. **`Too many columns in tabular`**: A row contains more `&` separators than declared in `\begin{tabular}{...}`.
3. **`Environment ... undefined`**: Missing `\usepackage` in the preamble (e.g., using `\multirow` without `\usepackage{multirow}`).
4. **`Missing \begin{document}`**: Commands placed before `\begin{document}` that belong inside the body.
5. **`File ... not found`**: Graphic file path or extension in `\includegraphics` is invalid.

---
*Summary documentation compiled for Technical Writing course requirements (MNIT Jaipur).*
