- [References](#references)
- [Introduction](#introduction)
  - [What is HTML?](#what-is-html)
  - [What is HTML5?](#what-is-html5)
  - [HTML: The Living Language](#html-the-living-language)
  - [Principles of HTML5](#principles-of-html5)
  - [Common HTML Terms](#common-html-terms)
    - [How they are used](#how-they-are-used)
- [The HTML5 Syntax](#the-html5-syntax)
  - [The HTML Skeleton](#the-html-skeleton)
    - [The Doctype](#the-doctype)
      - [Quirks Mode and Standards Mode](#quirks-mode-and-standards-mode)
    - [Character Encoding](#character-encoding)
    - [Specifying Language](#specifying-language)
    - [The `<head>` element](#the-head-element)
    - [The `<body>` element](#the-body-element)
  - [Syntax Changes](#syntax-changes)
    - [Loosened Rules](#loosened-rules)
    - [Removed Elements](#removed-elements)
    - [Adapted Elements](#adapted-elements)
- [Working with HTML](#working-with-html)
  - [Comments](#comments)
  - [Block and Inline Elements](#block-and-inline-elements)
  - [Divs and Spans](#divs-and-spans)
  - [Semantic Elements](#semantic-elements)
    - [Using Text-Based Elements](#using-text-based-elements)
      - [Headings](#headings)
      - [Paragraphs](#paragraphs)
      - [Bold Text (`<strong>` and `<em>`)](#bold-text-strong-and-em)
      - [Italic Text (`<em>` and `<i>`)](#italic-text-em-and-i)
    - [Structurally-based Elements](#structurally-based-elements)
      - [Header](#header)
      - [Navigation](#navigation)
      - [Article](#article)
      - [Section](#section)
      - [Aside](#aside)
      - [Footer](#footer)
  - [General HTML Elements](#general-html-elements)
    - [Creating Hyperlinks](#creating-hyperlinks)
      - [The anchor `<a>` element](#the-anchor-a-element)
      - [Relative and Absolute Paths](#relative-and-absolute-paths)
      - [Linking Email Addresses](#linking-email-addresses)
      - [Open Links in a New Window](#open-links-in-a-new-window)
      - [Linking to parts of the same page](#linking-to-parts-of-the-same-page)

# References
> HTML5: The Missing Manual, *2nd Edition* by Matthew MacDonald  
> 
> Learn to Code HTML and CSS: Develop and Style Websites by Shay Howe 
>  
> Learning Web Design: A Beginner's Guide to HTML, CSS, JavaScript and Web Graphics, *4th Edition* by Jennifer Niederst Robbins
> 

# Introduction

## What is HTML?
HTML stands for the *HyperText Markup Language*.  It is the (markup) language used to create web page documents. 

A markup language is basically used for formatting documents or (web) content. It gives content structure and meaning by adding descriptive tags to the document.

HTML defines text elements that make up documents such as headings, paragraphs, emphasized text, links, etc.

## What is HTML5?
HTML5 is really a web of interrelated standards. 
1. **Core HTML5** - This makes up the official W3C version of the specification. It includes new semantic elements, new and enhanced web form widgets, audio and video support, and the canvas for drawing with JavaScript.
2. **Features that were once HTML5** - Features that sprang form the original HTML5 spec as prepared by the WHATWG. These are mostly specifications for features that require JS and support rich web applications - data storage, offline applications and messaging.
3. **Features that are sometimes called HTMl5** - Next-gen features often lumped together with HTML5, even though they were never a part of the standard - CSS3 and geolocation.

## HTML: The Living Language
This means that an HTML page will never become obsolete and stop working. HTML pages will never use a version number, and developers will never need to 'upgrade' their markup from one version to another.  
By the same token, new features may be added to HTML at any time.

## Principles of HTML5
1. **Don't Break the Web**: A standard shouldn't introduce changes that makes other people's web pages stop working.  
2. **Pave the cowpaths**: HTML5 standardizes unofficial, but widely used techniques.
3. **Be practical**: Changes should have a practical purpose. The more demanding a change, the bigger the payoff needs to be.

## Common HTML Terms
1. **Elements**: Elements are designators that define the structure and content of objects. They are identified by the use of less-than and greater-than angle brackets surrounding the element name.

2. **Tags**: Tags comprise of the use of less-than and greater-than angle brackets surrounding an element. Tags mostly occur in pairs of opening and closing tags.

3. **Attributes**: Properties used to add additional information about an element. Attributes are defined within the opening tag, after an element's name. They generally include a name an a value. Examples are 
  * `class`: Classifies an element
  * `id`: Identifies an element
  * `src`: Specifies a source for an embeddable content.
  * `href`: Provides a hyperlink reference to a linked resource

### How they are used

```html
<a href="https://google.com">Google</a>
<element-name attribute="attribute-value">Element Content</element-name>
```
* `<a>` - the opening tag
* `a` - element (name)
* `href` - attribute (the hyperlink reference attribute)
* `https://google.com` - the attribute value
* `Google` - element content
* `</a>` - closing tag

* `<a>...</a>` - element


# The HTML5 Syntax

## The HTML Skeleton
The simplest HTML5 document you can create
```html
<!DOCTYPE html>
  <title>Document</title>
  <p>Learning to use HTML5</p>
```

This is more fleshed out
```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
</head>
<body>
  <p>Learning to use HTML5</p>
</body>
</html>
```
### The Doctype
The doctype clearly indicates the standard that was used to write the document markup that follows.  It indicates what version of HTML is being used and is placed at the beginning of the HTML document.
Despite the fact that HTML is a living language, the doctype remains. Without a doctype, most browsers will lapse into *quirks mode*, which differs from browser to browser.  
When you add a doctype, the browser recognises that you want to use the stricter standards mode, ensuring consistent formatting and layout on every modern browser.

Other agents such as HTML5 validators, search engines, design tools, and other human beings also make use of the doctype to determine what flavor of markup you're using.


#### Quirks Mode and Standards Mode


### Character Encoding
A standard that tells a computer how to convert your text into a sequence of bytes when it's stored in a file, and how to convert it back again when the file is opened.

Traditionally, on (English) websites, the encoding used is called **UTF-8**. It's compact, fast and supports all on-English characters you could need.

### Specifying Language
It's advisable to specify the language used for the web page. This is useful, especially for search engines when filtering search results.  
This can also help screen readers if a page has text from multiple languages, by indicating the languages of different sections.

To specify the language of content, you can add the `lang` attribute to any element, along with the appropriate language code.

### The `<head>` element
Identifies the top of the document, and includes any metadata. The content in the `<head>` is not displaye don the web page.
The document title is also included here and is displayed om the tile bar in the browser window. It also includes links to external files.

### The `<body>` element
All visible content appears here.

## Syntax Changes

### Loosened Rules
1. The `<html>`, `<head>` and `<body>` elements are optional. However, they are pretty useful so best to keep in.
2. Capitalization, when writing tags, is ignored. So `<EM></eM>` is allowed.
3. The closing slash can be omitted from a *void element*. *Void elements are elements with no nested content. Examples are `<br>`, `<img>` and `<hr>`* So `<br>`, `<br />` and `<br/>` are valid.
4. Attributes do not require quotation marks unless it contains a restricted character (such as >, = or a space).
   `<img alt="Horsehead Nebula" src=Horsehead01.jpg>`
5. Attributes with no values are allowed. So
   `<input type="checkbox" checked="checked">` and
   `<input type="checkbox" checked>` are valid.

### Removed Elements
1. **Presentational Elements (and Attributes)**: These are elements simply there to add formatting. Examples include `<strike>`, `<big>`, `<center>`, `<font>`, `<tt>`.
2. `<frames>` replaced by  `<iframe>`; used for displaying a web page in another web page.
3. `<acronym>` replaced by `<abbr>`
4. `<applet>` replaced by `<object>`

### Adapted Elements
Elements adapted to a new purpose.

1. `<small>` now represents small print, e.g legalese at the bottom of a contract.
2. `<hr>` represents a thematic break - a transition to another topic.
3. `<s>` represents text no longer accurate or relevant.
4. `<strong>` represents text with strong importance; text that needs to stand out from its surroundings.
5. `<b>` represents text that should be bold but has no greater important than the rest of the text. Could include keywords, product names, anything else that would be bold in print.
6. `<em>` represents with emphatic stress; text that might have a different inflection when read out loud.
7. `<i>` for italic text with no greater importance.

# Working with HTML

## Comments
```html
<!--This is a comment in HTML-->
```

```css
/*This is a comment in CSS*/
```

Any content wrapped in a comment is not displayed on the web page.

## Block and Inline Elements
*Block-level elements* begin on a new line, stacking on top of each other, and occupy any available width. Block-level elements may be nested inside one another and may wrap inline-level elements. They are mainly used for larger pieces of content.

*Inline-level elements* do not begin on a new line. They fall into the normal flow of a document, lining up one after the other, and only maintain the width of their content. Inline-level elements may be nested inside one another, but cannot wrap block-level elements.

## Divs and Spans
Divisions `<div>` and spans `<span>` are HTML elements that act as containers solely for styling purposes. They actually don't hold any semantic value.

A `<div>` is a block-level element that is commonly used to identify large groupings of content.

A `<span>` is an inline-level element commonly used to identify smaller groupings of text within a block-level element.

Divs and spans are commonly used with `class` or `id` attributes for styling purposes.



## Semantic Elements
*Semantics*, within HTML, is the practice of giving content on the page meaning and structure by using the proper element.

Semantic code describes the value of content on a page, regardless of the style or appearance of the element.



### Using Text-Based Elements

#### Headings
Headings are block-level elements, and they come in six different rankings, `<h1>` through `<h6>`. They are used to establish hierarchy.

Headings should be used in an order relevant to the content of a page. The primary heading of a page or section should be marked up with an `<h1>` elements, and subsequent headings should use `<h2>` through `<h6>` elements as necessary.

```html
<h1>Heading Level 1</h1>
<h2>Heading Level 2</h2>
<h3>Heading Level 3</h3>
<h4>Heading Level 4</h4>
<h5>Heading Level 5</h5>
<h6>Heading Level 6</h6>
```
![Headings](img/html-headings.png)

#### Paragraphs
Paragraphs are defined using the `<p>` block-level element.

```html
<p>Social norm: A pattern of behavior in a particular group, community, or culture, accepted as normal to which an individual is expected to conform.</p>

<p>Counterculture: a way of life and set of attitudes opposed to or at variance with the prevailing social norm.</p>
```
![Paragraphs](img/html-paragraphs.png)

#### Bold Text (`<strong>` and `<em>`)
These are both inline elements. 

The `<strong>` element is semantically used to give strong importance to text.

The `<b>` element is used to stylistically offset text.

They however look very similar.

```html
<!--Strong Importance-->
<p><strong>Caution:</strong> Falling Rocks.</p>

<!--Stylistically Offset-->
<p>This recipe calls for <b>bacon</b> and <b>mayonnaise</b>. </p>
```
![Bold Text](img/html-bold-text.png)

#### Italic Text (`<em>` and `<i>`)
The `<em>` element is used semantically to place a stressed emphasis on text.

The `<i>` element is used semantically to convey text in an alternative voice or tone, almost as if it were placed in quotation marks.

They however look very similar.
```html
<!--Stressed emphasis-->
<p>I <em>love</em> Chicago</p>

<!--Alternative voice or tone-->
<p>The name <em>Shay</em> means a gift.</p>
```

### Structurally-based Elements

These are all block-level elements that do not have any implied position or style. They can be used multiple times per page, so long as it reflects the proper semantic meaning.

![Structural Semantics](img/html-structural-semantics.png)

#### Header

The `<header>` element is used to identify the top of a page, article, section, or other section of a page. The `<header>` element may include a heading, introductory text, and even navigation.

```html
<!--Possible Section Header-->
<header>
  <h1>This is a header</h1>
</header>

<header>
<!--Typical Page Header-->
  <nav>
    <ul>
      <li>Home</li>
      <li>About Us</li>
      <li>Contact Us</li>
    </ul>
  </nav>
</header>
```

#### Navigation
The `<nav>` element identifies a section of major navigational links on a page. It's usually reserved for primary navigation sections only, such as global navigation, a table of contents, previous/next links.

Commonly, links within the `<nav>` element link to other pages within the same website or to other parts of the same web page. Miscellaneous one-off links should be wrapped in the anchor `<a>` element.

```html
  <nav>
    <ul>
      <li>Home</li>
      <li>About Us</li>
      <li>Contact Us</li>
    </ul>
  </nav>
```

#### Article

The `<article>` element is used to identify a section of self-content that may be independently distributed or reused. It's often used to mark up blog posts. newspaper articles, user-submitted content, etc.

To decide if the `<article>` tag should be used, the content should be such that could be replicated elsewhere without any confusion. If the content  is removed from the context of the page and placed somewhere else, it should still make sense.

#### Section

The `<section>` element is used to identify a thematic grouping of content, that is content that makes sense to be together under a certain sub-heading or as sub-headings or discussions under a particular topic. 

The content placed in the `<section>` element should make sense as contributing as a part of a whole topic. It is commonly used to break up and provide hierarchy to a page, and usually contains a heading.


#### Aside

The `<aside>` element holds information that is tangentially related to the content surrounding it. Example: sidebars, inserts or brief explanation.

The `<aside>` element can be thought of as appearing to the left or right side of a page.

#### Footer
The `<footer>` element identifies the end of a page, article, section or other segment of a page.

## General HTML Elements

### Creating Hyperlinks

#### The anchor `<a>` element

The `<a>` element is used to create hyperlinks. Hyperlinks provide the ability to link from one web page or resource to another.

To create a link, the `href` attribute (a hyperlink reference) is required. The `href` attribute identifies the destination of the link.

`<a href="http://shayhowe.com">Shay</a>`

![HTML Anchor](img/html-anchor.png)

The `<a>` element is an inline element. However, with the introduction of HTML5, anchor elements can wrap block, inline or other level elements.

#### Relative and Absolute Paths

Links pointing to other pages of the same website have a *relative path*. The `href` attribute needs to include the file name and/or directory as the case may be.

Links pointing to other website require an absolute path. The `href` attribute needs to include the full domain.

```html
<!-----Relative Paths------>

<!--If file is in the same folder-->
<a href="about.html">About</a> 

<!--If file is in the same folder-->
<a href="about.html">About</a> 

<!------Absolute Paths------>
<a href="http://www.google.com">Google</a>
```
#### Linking Email Addresses

```html
<a href="mailto:umana.mmedara@gmail.com">Email Me</a>

<!--To add a subject line (Reaching Out)-->
<a href="mailto:umana.mmedara@gmail.com?subject=Reaching20%Out">Email Me</a>

<!--To add body text (How are you)-->
<a href="mailto:umana.mmedara@gmail.com?subject=Reaching20%Out&body=How%20are%20you">Email Me</a>
```

The `?` after the email address is necessary to bind the next parameter to the hyperlink path.

The `&` after the `subject` parameter is to seperate the `body` parameter from it.

Spaces are encoded using `%20` and line breaks are encoded using `%0A`.

#### Open Links in a New Window

`<a href="http://google.com" target="_blank">Google</a>`

Hyperlinks have the ability to determine where a link opens when clicked. This requires the `target` attribute. 

The `_blank` value indicates a new window.

#### Linking to parts of the same page

This required the use of an `id` attribute on the element you're trying to link to.

```html
<body id="top">
...
<a href="#top">Back to top</a>
...
</body>
```
