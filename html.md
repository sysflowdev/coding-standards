---
title: HTML
---
# HTML

- [Introduction](#introduction)
- [Be Smart and Future Proof](#be-smart)
- [Standards](#standards)
    - [Use Correct Document Type](#document-types)
    - [Use Lower Case Element Names](#lower-case-element-names)
    - [Close All HTML Elements](#close-html-elements)
    - [Close Empty HTML Elements](#close-empty-html-elements)
    - [Use Lower Case Attribute Names](#lower-case-attribute-names)
    - [Quote Attribute Values](#quote-attribute-values)
    - [Image Attributes](#image-attributes)
    - [Spaces and Equal Signs](#spaces-equal-signs)
    - [Avoid Long Code Lines](#avoid-long-code-lines)
    - [Blank Lines and Indentation](#blank-lines-and-indentation)
    - [Do Not Omit `<html>` and `<body>`?](#omitting-html-body-tags)
    - [Do Not Omit `<head>`?](#omitting-head)
    - [Meta Data](#meta-data)
    - [Setting The Viewport](#set-viewport)
    - [HTML Comments](#html-comments)
    - [Style Sheets](#style-sheets)
    - [Loading JavaScript in HTML](#load-javascript-in-html)
    - [Accessing HTML Elements with JavaScript](#access-html-elements-in-javascript)
    - [Use Lower Case File Names](#use-lower-case-file-names)
    - [File Extensions](#file-extensions)
        - [Differences Between .htm and .html](#differences-html-htm)
        - [Technical Differences](#technical-differences)

<a name="introduction"></a>
## Introduction
Most of our websites define themselves as HTML5 (via their doctypes), therefore our standards are aimed at HTML5 whilst being backwards compatibility and future-proof as HTML5 allows you to be lazy.

<a name="be-smart"></a>
## Be Smart and Future Proof
A consistent use of style, makes it easier for others to understand your HTML.

In the future, programs like XML readers, may want to read your HTML.

Using a well-formed "close to XHTML" syntax, is smart as it makes sites backwards compatible and future proof.

> {tip} Always keep your code tidy, clean, and well-formed.

<a name="standards"></a>
## Standards
<a name="document-types"></a>
### Use Correct Document Type
Always declare the document type as the first line in your document:

```
<!DOCTYPE html>
```

If you want consistency with lower case tags, you can use:

```
<!doctype html>
```
<a name="lower-case-element-names"></a>
### Use Lower Case Element Names
HTML5 allows mixing uppercase and lowercase letters in element names.

We recommend using lowercase element names because:

- Mixing uppercase and lowercase names is bad
- Developers normally use lowercase names (as in XHTML)
- Lowercase look cleaner
- Lowercase are easier to write

**Bad:**
```
<SECTION> 
  <p>This is a paragraph.</p>
</SECTION>
```
**Very Bad:**
```
<Section> 
  <p>This is a paragraph.</p>
</SECTION>
```
**Good:**
```
<section> 
  <p>This is a paragraph.</p>
</section>
```

<a name="close-html-elements"></a>
### Close All HTML Elements
Always close all HTML elements.

**Bad:**
```
<section>
  <p>This is a paragraph.
  <p>This is a paragraph.
</section>
```
**Good:**
```
<section>
  <p>This is a paragraph.</p>
  <p>This is a paragraph.</p>
</section>
```

<a name="close-empty-html-elements"></a>
### Close Empty HTML Elements
Always close empty HTML elements.

**Allowed:**
`<meta charset="utf-8">`
**Also Allowed:**
`<meta charset="utf-8" />`


<a name="lower-case-attribute-names"></a>
### Use Lower Case Attribute Names
Always use lowercase attribute names because:

- Mixing uppercase and lowercase names is bad
- Developers normally use lowercase names (as in XHTML)
- Lowercase look cleaner
- Lowercase are easier to write

**Bad:**
```
<div CLASS="menu">
```
**Good:**
```
<div class="menu">
```

<a name="quote-attribute-values"></a>
### Quote Attribute Values
HTML5 allows attribute values without quotes.

We recommend quoting attribute values because:

- Mixing uppercase and lowercase values is bad
- Quoted values are easier to read
- You MUST use quotes if the value contains spaces

**Very bad:**
This will not work, because the value contains spaces:
```
<table class=table striped>
```
**Bad:**
```
<table class=striped>
```
**Good:**
```
<table class="striped">
```

<a name="image-attributes"></a>
### Image Attributes
Always add the "alt" attribute to images. This attribute is important when the image for some reason cannot be displayed. Also, always define image width and height. It reduces flickering because the browser can reserve space for the image before loading.

**Bad:**
```
<img src="html5.gif">
```
**Good:**
```
<img src="html5.gif" alt="HTML5" style="width:128px;height:128px">
```

<a name="spaces-equal-signs"></a>
### Spaces and Equal Signs
HTML5 allows spaces around equal signs. But space-less is easier to read, and groups entities better together.

**Bad:**
```
<link rel = "stylesheet" href = "styles.css">
```
**Good:**
```
<link rel="stylesheet" href="styles.css">
```

<a name="avoid-long-code-lines"></a>
### Avoid Long Code Lines
When using an HTML editor, it is inconvenient to scroll right and left to read the HTML code.

Try to avoid code lines longer than 240 characters.

<a name="blank-lines-and-indentation"></a>
### Blank Lines and Indentation
Do not add blank lines without a reason.

For readability, add blank lines to separate large or logical code blocks.

For readability, add four spaces of indentation. Do not use the tab key.

Do not use unnecessary blank lines and indentation. It is not necessary to indent every element:

**Unnecessary:**
```
<body>

  <h1>Famous Cities</h1>

  <h2>Tokyo</h2>

  <p>
    Tokyo is the capital of Japan, the center of the Greater Tokyo Area,
    and the most populous metropolitan area in the world.
    It is the seat of the Japanese government and the Imperial Palace,
    and the home of the Japanese Imperial Family.
  </p>

</body>
```
**Better:**
```
<body>

<h1>Famous Cities</h1>

<h2>Tokyo</h2>
<p>Tokyo is the capital of Japan, the center of the Greater Tokyo Area,
and the most populous metropolitan area in the world.
It is the seat of the Japanese government and the Imperial Palace,
and the home of the Japanese Imperial Family.</p>

</body>
```

**Table Example:**

```
<table>
  <tr>
    <th>Name</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>A</td>
    <td>Description of A</td>
  </tr>
  <tr>
    <td>B</td>
    <td>Description of B</td>
  </tr>
</table>
```
**List Example:**
```
<ol>
  <li>London</li>
  <li>Paris</li>
  <li>Tokyo</li>
</ol>
```

<a name="omitting-html-body-tags"></a>
### Do Not Omit `<html>` and `<body>`?
> {note} Just because you can doesn't mean you should!

<a name="omitting-head"></a>
### Do Not Omit `<head>`?
> {note} Just because you can doesn't mean you should!

<a name="meta-data"></a>
### Meta Data
The `<title>` element is required in HTML5. Make the title as meaningful as possible:

```
<title>HTML5 Syntax and Coding Style</title>
```
To ensure proper interpretation, and correct search engine indexing, both the language and the character encoding should be defined as early as possible in a document:
```
<!DOCTYPE html>
<html lang="en-US">
<head>
  <meta charset="UTF-8">
  <title>HTML5 Syntax and Coding Style</title>
</head>
```

<a name="set-viewport"></a>
### Setting The Viewport
HTML5 introduced a method to let web designers take control over the viewport, through the <meta> tag.

The viewport is the user's visible area of a web page. It varies with the device, and will be smaller on a mobile phone than on a computer screen.

You should include the following `<meta>` viewport element in all your web pages:

```
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```
A `<meta>` viewport element gives the browser instructions on how to control the page's dimensions and scaling.

The width=device-width part sets the width of the page to follow the screen-width of the device (which will vary depending on the device).

The initial-scale=1.0 part sets the initial zoom level when the page is first loaded by the browser.

Here is an example of a web page without the viewport meta tag, and the same web page with the viewport meta tag:

<a name="html-comments"></a>
### HTML Comments
Short comments should be written on one line, like this:

```
<!-- This is a comment -->
```
Comments that spans more than one line, should be written like this:
```
<!-- 
  This is a long comment example. This is a long comment example.
  This is a long comment example. This is a long comment example.
-->
```
Long comments are easier to observe if they are indented four spaces.

<a name="style-sheets"></a>
### Style Sheets
Use simple syntax for linking to style sheets (the type attribute is not necessary):

```
<link rel="stylesheet" href="styles.css">
```
Short rules can be written compressed, on one line, like this:

```css
p.intro {font-family: Verdana; font-size: 16em;}
```
Long rules should be written over multiple lines:
```css
body {
  background-color: lightgrey;
  font-family: "Arial Black", Helvetica, sans-serif;
  font-size: 16em;
  color: black;
}
```
- Place the opening bracket on the same line as the selector
- Use one space before the opening bracket
- Use four spaces of indentation
- Use semicolon after each property-value pair, including the last
- Only use quotes around values if the value contains spaces
- Place the closing bracket on a new line, without leading spaces
- Avoid lines over 80 characters

<a name="load-javascript-in-html"></a>
### Loading JavaScript in HTML
Use simple syntax for loading external scripts (the type attribute is not necessary):
```
<script src="myscript.js">
```

Also use schema-less links when linking when providing absolute paths.
```
<script src="//ajax.googleapis.com/ajax/libs/angularjs/1.6.4/angular.min.js"></script>
```

<a name="access-html-elements-in-javascript"></a>
### Accessing HTML Elements with JavaScript
A consequence of using "untidy" HTML styles, might result in JavaScript errors.

These two JavaScript statements will produce different results:

**Example**
```javascript
var obj = getElementById("Demo")
```

```javascript
var obj = getElementById("demo")
```

<a name="use-lower-case-file-names"></a>
### Use Lower Case File Names
Some web servers (Apache, Unix) are case sensitive about file names: "london.jpg" cannot be accessed as "London.jpg".

Other web servers (Microsoft, IIS) are not case sensitive: "london.jpg" can be accessed as "London.jpg" or "london.jpg".

If you use a mix of upper and lower case, you have to be extremely consistent.

If you move from a case insensitive to a case sensitive server, even small errors will break your web!

To avoid these problems, always use lower case file names.

<a name="file-extensions"></a>
### File Extensions
HTML files should have a **.html** or **.htm** extension.

CSS files should have a **.css** extension.

JavaScript files should have a **.js** extension.

<a name="differences-html-htm"></a>
#### Differences Between .htm and .html
There is no difference between the .htm and .html extensions. Both will be treated as HTML by any web browser or web server.

The differences are cultural:

.htm "smells" of early DOS systems where the system limited the extensions to 3 characters.

.html "smells" of Unix operating systems that did not have this limitation.

<a name="technical-differences"></a>
#### Technical Differences
When a URL does not specify a filename (like https://www.w3schools.com/css/), the server returns a default filename. Common default filenames are index.html, index.htm, default.html, and default.htm.

If your server is configured only with "index.html" as default filename, your file must be named "index.html", not "index.htm."

However, servers can be configured with more than one default filename, and normally you can set up as many default filenames as needed.

Anyway, the full extension for HTML files is .html, and there's no reason it should not be used.