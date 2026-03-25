# SimpleSystemTeX

**An automated file & block management system for large-scale LaTeX typesetting.**

**SimpleSystemTeX** is a LaTeX package built on LaTeX3, specifically designed for large-scale, integrated typesetting tasks. Its core design philosophy is to maximize the **separation of content and structure**. 

By freeing creators from constantly managing global document structure, anchors, and stylistic details, this package significantly reduces the maintenance burden of large documents. This approach is particularly beneficial for boosting efficiency when utilizing AI tools for text polishing or assisting.

## Key Features

- **Automated File Management:** Treat "Sections" as independent subfiles. Import them sequentially to automatically build your document body.
- **Auto-Generated TOC:** Easily generate a Table of Contents (`\TableofContents`) that dynamically adapts to the sequence of your imported section files.
- **Block & Cross-Reference Integration:** Declare regular and anonymous block types (e.g., Theorems, Definitions, Proofs). Creating a block automatically generates anchors, allowing you to link them effortlessly without manually managing `\label` and `\ref`.
- **Automated Indexing:** Quickly generate indices for specific block types within any specific group/directory scope (`\MakeBlockIndex`).
- **Highly Flexible Styling Engine:** A powerful `\SetStyle` command that supports standard LaTeX commands, special display arguments (e.g., `@sectionname`), and conditionals (e.g., `#ifempty`) to customize the appearance of TOCs, headings, blocks, and links.

## Building from Source

This project utilizes the standard LaTeX3 build system. If you are cloning this repository or downloading the raw source code, you can open your terminal in the project's root directory and run

```bash
l3build unpack
```

to generate the `simplesystemtex.sty` package file from the source files.

This command will use the included `build.lua` script to automatically process the source files and extract the ready-to-use `simplesystemtex.sty` file.

## Typical Directory Structure

The system relies on a clean directory structure. By default, it looks for section files in the `./sec/` directory:

```text
Project/
├── main.tex                 % Your main LaTeX file
├── simplesystemtex.sty      % The package file (if not installed globally)
└── sec/
    └── Group/               % Top-level group
        ├── Subgroup/        % Second-level group
        │   ├── Section1.tex % Section file
        │   └── Section2.tex
```

## Quick Start

### 1. Main File (`main.tex`)
```latex
\documentclass{article}
\usepackage{simplesystemtex}

% Declare block types in the preamble
\NewBlockType{Theorem}
\NewBlockType*{Proof}

\begin{document}

% Generate the Table of Contents
\TableofContents

% Import sections (Paths are relative to the default './sec/' prefix)
\AddPart{Part A: Introduction}
\ImportSection{Group/Subgroup/Section1}(Custom Display Name)

\end{document}
```

### 2. Section File (`sec/Group/Subgroup/Section1.tex`)
Write your content using the declared block commands. 

```latex
\Theorem{thm-euler}{Euler's Identity}{
    $e^{i\pi} + 1 = 0$
}

\Proof(Proof of Identity){
    As we can see from \blclink{thm-euler}, the relationship between these fundamental constants is elegant...
}

% Insert a block index anywhere
\MakeBlockIndex{Group/Subgroup}[Theorem]
```

## Documentation

For comprehensive details on all commands, advanced styling configurations, and predefined styles, please refer to the official manual: `simplesystemtex.doc.pdf`.

## Repository & Bug Tracker

- **GitHub Repository:** [https://github.com/JokerXin2025/SimpleSystemTeX](https://github.com/JokerXin2025/SimpleSystemTeX)
- **Author:** JokerXin2025 (<jokerxin2025@163.com>)

## License

This material is subject to the LaTeX Project Public License (LPPL), version 1.3c or later.