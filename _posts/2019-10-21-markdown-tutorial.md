---
layout: post
title: Markdown Tutorial
date: 2019-10-22 14:26:00 +0800
tags: IT    
---

## What is Markdown
Markdown is a lightweight markup language with plain-text-formatting syntax which is often used to format readme files, for writing messages in online discussion forums, and to create rich text using a plain text editor.

## Basic Syntax
### Title  
H1 :`# Header 1`  
H2 :`## Header 2`  
H3 :`### Header 3`  
H4 :`#### Header 4`  
H5 :`##### Header 5`  
H6 :`###### Header 6`  
### Font Style  
Link :[Title](URL) `[Title](URL)`  
Bold :**Bold** `**Bold**`  
Italics :*Italics* `*Italics*`  
Code Line :~~text~~ `~~text~~`  
### List  
* List1
* List2
* List3

```
* List1
* List2
* List3
```
### Images
![Alternative text when images is not available](/images/posts/markdown/img1.jpg)
```
![Alternative text when images is not available](/images/posts/markdown/img1.jpg)
```
### Others  
Escape Character: \  
New Line: Put at least two space before \n in plain text  
Code in Line : Use \`\` to quote the code `print 'Hello World'`

## Extended Syntax  
### Task Lists
- [x] Write the press release
- [ ] Update the website
- [ ] Contact the media

```
- [x] Write the press release
- [ ] Update the website
- [ ] Contact the media
```
### Fenced Code Blocks  
```
{
  "firstName": "John",
  "lastName": "Smith",
  "age": 25
}
```
### Table  

| Syntax      | Description | Test Text     |
| :---        |    :----:   |          ---: |
| Header      | Title       | Here's this   |
| Paragraph   | Text        | And more      |

```
| Syntax      | Description | Test Text     |
| :---        |    :----:   |          ---: |
| Header      | Title       | Here's this   |
| Paragraph   | Text        | And more      |
```

For more basic and extended syntax, please refer to [Markdown Guide](https://www.markdownguide.org/) for more details.

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

$$ \frac{-b\pm\sqrt{b^2-4ac}}{2a} $$
