---
layout: post
title: Markdown Tutorial
date: 2019-10-22 14:26:00 +0800
tags: Markdown    
---

## What is Markdown


## Basic Syntax
[Markdown Guide](https://www.markdownguide.org/basic-syntax/) lists basic syntax of markdown like _Headings_, _Links_, _Images_, _Tables_ and so on.
Refer to the website for more details.

## Formulation Syntax
While markdown offers a convenient way to edit text, it is not good at display equatioans and formulations by itself.
To type formulation in markdown, the basic idea is taking advantage of inline HTML which is supported in markdown.
Inline HTML can be used for both simple inline eqations and, with external tool, more complex rendering.
Below are summary of original [answer](https://stackoverflow.com/questions/11256433/how-to-show-math-equations-in-general-githubs-markdownnot-githubs-blog).

### Simple Inline
HTML ampersand [entity codes](https://www.w3schools.com/html/html_entities.asp) provided unique codes for both reserved characters and characters that are not present on keyboard.
Find the entity codes for common [math symbols](https://sites.psu.edu/symbolcodes/codehtml/#math) and [Greek letters](https://www.keynotesupport.com/internet/special-characters-greek-letters-symbols.shtml) on the hyperlink respectively.
Following is an example of how to using these entity codes to express: h<sub>&theta;</sub>(x) = &theta;<sub>o</sub> x + &theta;<sub>1</sub>x

```html
    h<sub>&theta;</sub>(x) = &theta;<sub>o</sub> x + &theta;<sub>1</sub>x
```


### Complex Inline
For more complex equations, an external LaTex renderer like [CodeCogs](https://www.codecogs.com/latex/eqneditor.php) are needed.
CodeCogs receives LaTex format text for equations and compiled them into image format.
Choose HTML embed code at the bottom of the page and paste the embed code from dialogue into markdown to cite the images of equations.
Following is an example of express:  
<img src="https://latex.codecogs.com/svg.latex?x&space;=&space;\frac{-b\pm\sqrt{b^2-4ac}}{2a}" title="x = \frac{-b\pm\sqrt{b^2-4ac}}{2a}" />  
The corresponding HTML embed code is:

```html
<img src="https://latex.codecogs.com/svg.latex?x&space;=&space;\frac{-b\pm\sqrt{b^2-4ac}}{2a}" title="x = \frac{-b\pm\sqrt{b^2-4ac}}{2a}" />
```


### Multi-line Rendering
If multi-line rendering is needed, check out this [answer](https://stackoverflow.com/questions/35498525/latex-rendering-in-readme-md-on-github/41341966#41341966)