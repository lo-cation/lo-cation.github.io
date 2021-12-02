---
layout: post
title:  Configuration for vscode+latex+sumatraPDF
date:   2021-12-02 12:00:00 +0800
tags: IT
---
Here is a tutorial of configuring latex environment on Windows machine using vscode+texlive+SumatraPDF.

## Prerequisites
1. [texlive 2021-20210325](https://mirrors.tuna.tsinghua.edu.cn/CTAN/systems/texlive/Images/)
2. [vscode 1.62.3 (user setup)](https://code.visualstudio.com/)
3. [SumatraPDF 3.3.3](https://www.sumatrapdfreader.org/)

## Install texlive
Installation package can be downloaded from the [Tsinghua Open Source Mirror](https://mirrors.tuna.tsinghua.edu.cn/CTAN/systems/texlive/Images/). The version used in this tutorial is `texlive2021-20210325`. The installation is straight forward, just following the instruction would be fine.
![](/images/posts/IT/20211202-texlive.jpg)

## Install vscode and relative extension
Installation package can be downloaded from the [Official website](https://code.visualstudio.com/). The version used in this tutorial is `1.62.3 (user setup)`. Just follow the instruction to complete the installation and remember to keep the installation path `$VSCODEPATH` in mind for it will be used in the configuration file introduced later. After installation of vscode, one can find an extension named `Markdown Preview Enhanced` from the extensions market which provides useful functions for preview.
![](/images/posts/IT/20211202-vscode.jpg)

## Install SumatraPDF
Installation package can be downloaded from the [Official website](https://www.sumatrapdfreader.org/). Remember the installation path `$SUMATRAPATH` as well.

## Configuration
1. `Ctrl+Shift+P`, type in `json` and select `Preference: Open settings (JSON)` to open the configuration.
2. Copy the following code into the file opened previously.
```json
{
        // ======================== LaTeX Configuration BEGIN  ========================
        // bibtex format
        "latex-workshop.bibtex-format.tab": "tab",
     
        // Close auto build of latex
        "latex-workshop.latex.autoBuild.run": "never",
        "latex-workshop.latex.autoBuild.cleanAndRetry.enabled": false,
     
        // Set PDF preview program
        "latex-workshop.view.pdf.viewer": "external",
        "latex-workshop.view.pdf.ref.viewer": "external",
        "latex-workshop.view.pdf.external.viewer.command": "$SUMATRAPATH/SumatraPDF.exe", // Change path to the installation path of SumatraPDF
        "latex-workshop.view.pdf.external.viewer.args": [
            "%PDF%"
        ],
     
        // Forward search and inverse search
        "latex-workshop.view.pdf.external.synctex.command": "$SUMATRAPATH/SumatraPDF.exe", // Change path to the installation path of SumatraPDF
        "latex-workshop.view.pdf.external.synctex.args": [
            // forward search
            "-forward-search",
            "%TEX%",
            "%LINE%",
            "-reuse-instance",
            // inverse search
            "-inverse-search",
            "\"$VSCODEPATH\\Code.exe\" -r -g \"%f:%l\"", // Change path to the installation path of vscode
            "%PDF%"
        ],
 
        // Compile schemes
        "latex-workshop.latex.tools": [
            {
                // Native complie schemes of Windows TeX Live 2021
                "name": "Windows XeLaTeX",
                "command": "xelatex",
                "args": [
                    "-synctex=1",
                    "-interaction=nonstopmode",
                    "-file-line-error",
                    "-pdf",
                    "%DOCFILE%"
                ]
            },
            {
                // Windows Biber compiler
                "name": "Windows Biber",
                "command": "bibtex",
                "args": [
                    "%DOCFILE%"
                ]
            },
            {
                // WSL XeLaTeX which contains Chinese
                "name": "WSL XeLaTeX",
                "command": "wsl",
                "args": [
                    //"/usr/local/texlive/2020/bin/x86_64-linux/xelatex",
                    "C:/texlive/2021/bin/win32/xelatex",
                    "-synctex=1",
                    "-interaction=nonstopmode",
                    "-file-line-error",
                    "-pdf",
                    //"-output-directory=%OUTDIR%",
                    //"-aux-directory=%OUTDIR%",
                    "%DOCFILE%"
                ]
            },
            {
                // WSL biber / bibtex compile with citation notation
                "name": "WSL Biber",
                "command": "wsl",
                "args": [
                    //"/usr/local/texlive/2020/bin/x86_64-linux/biber",
                    "C:/textlive/2021/bin/win32/biber",
                    "%DOCFILE%"
                ]
            },
        ],
     
        // Compile schemes which will be displaied in GUI
        "latex-workshop.latex.recipes": [
            {
                "name": "Windows XeLaTeX 简单编译",
                "tools": [
                    "Windows XeLaTeX"
                ]
            },
            {
                "name": "Windows xe->bib->xe->xe 复杂编译",
                "tools": [
                    "Windows XeLaTeX",
                    "Windows Biber",
                    "Windows XeLaTeX",
                    "Windows XeLaTeX"
                ]
            },
            {
                "name": "XeLaTeX 简单编译",
                "tools": [
                    "WSL XeLaTeX"
                ]
            },
            {
                "name": "xe->bib->xe->xe 复杂编译",
                "tools": [
                    "WSL XeLaTeX",
                    "WSL Biber",
                    "WSL XeLaTeX",
                    "WSL XeLaTeX"
                ]
            },
        ],
     
        // clean temp files
        "latex-workshop.latex.clean.fileTypes": [
            "*.aux",
            "*.bbl",
            "*.blg",
            "*.idx",
            "*.ind",
            "*.lof",
            "*.lot",
            "*.out",
            "*.toc",
            "*.acn",
            "*.acr",
            "*.alg",
            "*.glg",
            "*.glo",
            "*.gls",
            "*.ist",
            "*.fls",
            "*.log",
            "*.fdb_latexmk",
            "*.bcf",
            "*.run.xml",
            //"*.synctex.gz"
        ],
        "security.workspace.trust.untrustedFiles": "open"
    // ======================== LaTeX Configuration END ========================
}
```
3. Remeber to replace the `VSCODEPATH` and `SUMAPTAPATH` in the above code.
4. `Ctrl+Alt+B` to compile latex project.
5. For forward search, place the cursor before the word to be searched in tex file and use shortcut `Ctrl+Shift+J`
6. For inverse search, open SumatraPDF first, then choose external preview from GUI of vscode. Double-click the word to be searched in SumatraPDF.