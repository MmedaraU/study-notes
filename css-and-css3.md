- [References](#references)
- [Introduction](#introduction)
  - [Common CSS Terms](#common-css-terms)
  - [Anatomy of a Style](#anatomy-of-a-style)
  - [Referencing CSS](#referencing-css)
  - [Comments](#comments)
  - [CSS Resets](#css-resets)
- [Selectors](#selectors)
  - [Type Selectors](#type-selectors)
  - [Class Selectors](#class-selectors)
    - [Naming Classes](#naming-classes)
  - [ID Selectors](#id-selectors)
  - [Universal Selector](#universal-selector)
  - [Combining Selectors](#combining-selectors)
    - [Group Selectors](#group-selectors)
    - [Descendant Selectors](#descendant-selectors)
      - [Pseudo-Classes and Pseudo-Elements](#pseudo-classes-and-pseudo-elements)
        - [Pseudo-classes](#pseudo-classes)
          - [For links](#for-links)
          - [For others](#for-others)
        - [Pseudo-Elements](#pseudo-elements)
          - [For paragraphs](#for-paragraphs)
          - [For others](#for-others-1)
    - [Attribute Selectors](#attribute-selectors)
    - [Child Selectors](#child-selectors)
      - [Child Pseudo-elements](#child-pseudo-elements)
    - [SIbling Selector](#sibling-selector)
    - [The `:not()` selector](#the-not-selector)
- [Inheritance](#inheritance)
- [The Cascade](#the-cascade)
- [Specificity](#specificity)
  - [Overriding Specificity](#overriding-specificity)
- [Colors](#colors)
  - [Keyword Colors](#keyword-colors)
  - [Hexadecimal Color Notation](#hexadecimal-color-notation)
  - [RGB / RGBa](#rgb--rgba)
  - [HSL / HSLa](#hsl--hsla)
- [Measurement Values](#measurement-values)
  - [Absolute Units](#absolute-units)
    - [Pixels](#pixels)
  - [Relative Units](#relative-units)
    - [Keywords](#keywords)
    - [Percentages](#percentages)
    - [Ems](#ems)
- [Formatting Text](#formatting-text)
  - [Font Types/Formats](#font-typesformats)
  - [Properties](#properties)
    - [The `font-family` property](#the-font-family-property)
      - [Generic font families](#generic-font-families)
      - [Using self-hosted fonts](#using-self-hosted-fonts)
    - [The `color` property](#the-color-property)
    - [The `font-size` property](#the-font-size-property)
    - [The `font-style` property](#the-font-style-property)
    - [The `font-weight` property](#the-font-weight-property)
    - [The `font-variant` property](#the-font-variant-property)
    - [The `text-transform` property](#the-text-transform-property)
    - [The `text-decoration` property](#the-text-decoration-property)
    - [The `letter-spacing` and `word-spacing` property](#the-letter-spacing-and-word-spacing-property)
    - [The `text-shadow` property](#the-text-shadow-property)
    - [The `line-height` property](#the-line-height-property)
    - [The `text-align` property](#the-text-align-property)
    - [The `text-indent` property](#the-text-indent-property)
  - [The `font` shorthand](#the-font-shorthand)
- [Styling Lists](#styling-lists)
  - [The `list-style-type` property](#the-list-style-type-property)
  - [The `list-style-position` property](#the-list-style-position-property)
- [Margins, Paddings and Borders](#margins-paddings-and-borders)
  - [The Box Model](#the-box-model)
    - [The `display` property](#the-display-property)
    - [The `box-sizing` property](#the-box-sizing-property)
    - [The `width` and `height` property](#the-width-and-height-property)
    - [The `overflow` property](#the-overflow-property)
    - [The `box-shadow` property](#the-box-shadow-property)
  - [Margins](#margins)
    - [Collapsing Margins](#collapsing-margins)
  - [Padding](#padding)
  - [Borders](#borders)
- [The `float` property](#the-float-property)
  - [Clearing Floats `clear`](#clearing-floats-clear)

# References
> **Learn to Code HTML and CSS: Develop and Style Websites** by *Shay Howe*  
> 
> **CSS3: The Missing Manual** by *David Sawyer McFarland*
> 
<!-- > **Learning Web Design: A Beginner's Guide to HTML, CSS, JavaScript and Web Graphics, 4th Edition** by *Jennifer Niederst Robbins* -->


# Introduction
CSS stands for *Cascading Style Sheets*. It is a presentation language created to style the appearance of content.

## Common CSS Terms
1. **Selectors**: A selector designates exactly which element or elements within our HTML to target and apply styles to. Selectors can target an id, class or a type of element.

2. **Properties**: Determines the styles that will be applied to the element targeted. Examples include `color`, `width`, etc.

3. **Values**: A value determines the behaviour of a property. 

4. **Style sheet**: A collection of CSS styles. Basically, the entire CSS file.

## Anatomy of a Style
```css
p {
  color: orange;
}

selector {
  property: value;
}
```
* `p` - selector
* `color` - property
* `orange` - value
* `p {...}` - rule set / declaration block
* `color: orange;` - declaration

## Referencing CSS
1. Inline  
    Usually placed between HTML tags. Styles only apply to that element.
    ```html
    <h1 style="color:#666;"></h1>
    ```

2. Internal Style Sheets  
    Styles are part of HTML. It always appears between `<style>` tags in the `<head>` portion.
    ```html
      <head>
        ...
      <style>
        table {border-collapse: separate; border-spacing: 0;}
      </style>
      </head>
    ```

4. External style sheet  
    Done by linking an external CSS file (a plain text file with a `.css` file extension). This file should be saved within the same folder, or a subfolder, where the HTML is located.
    Here's how an external style sheet is linked
    ```html
      <head>
        <link rel="stylesheet" href="main.css">
      </head>
    ```
    OR Using the `@import` directive
    ```html
      <head>
        ...
      <style>
        @import url (css/styles.css);
      </style>
      </head>
    ```

**Note**: Imported styles have to be placed before internal styles, and before style in an external style sheet.
```html
  <style>
    @import url (css/styles.css);
  </style>
  
  <link rel="stylesheet" href="main.css">

  <style>
    table {border-collapse: separate; border-spacing: 0;}
  </style>
```
OR

```css
/*External Style Sheet - main.css*/
@import url (css/styles.css);
....
```

```html
<!--HTML-->
<head>
  <link rel="stylesheet" href="main.css">
...
  <style>
    table {border-collapse: separate; border-spacing: 0;}
  </style>
</head>
```
## Comments
```css
/*This is a comment in CSS*/
p {color:red;}
```
## CSS Resets
Every web browser has its own default styles for different styles. CSS Resets are used to ensure cross-browser compatibility.

CSS Resets take every common HTML elements and provides a unified styles for browsers. Resets generally involve removing any sizing. margins, paddings, etc and toning these values down.


# Selectors

## Type Selectors
Tag/Type/Element Selectors.  
Target selectors by their element type.
```html
<div>...</div>
```
```css
div {...}
```

## Class Selectors
Targets an element based on the class attribute. They are more specific than type selectors - select a particular group of elements rather than all elements of one type.  
This works really well with divs and spans.
```html
<div class="awesome">...</div>
```
```css
.awesome {...}
```

### Naming Classes
1. Only letters, numbers, hyphens, and underscores in class names.
2. A class name must begin with a letter
3. Class names are case sensitive

## ID Selectors
They are more precise than class selectors; targeting only one unique element at a time.

ID attribute values can only be used once per page.

Within CSS, the id selector is denoted by a leading hash sign (#) followed by the id attribute value.

```html
<div id="id-value">...</div>
```

```css
#id-value {...}
```

## Universal Selector
The asterisk (*) is the universal selector. It selects all tags.
```css
* {
  margin: 0;
  box-sizing: border-box;
}
```

## Combining Selectors

### Group Selectors
Selecting several selectors at the same time so the same style can be applied to them.
```css
h1, h2, h3 {
  color: #1e1e1e;
}
```

### Descendant Selectors
A descendant is a tag present in another tag, no matter where it's nested. Example, the `<html>` tag is a descendant of the `<body>` tag.

```css
div p {
  font-size: 1em;
}
```

This style rule is targeting all paragraphs in divs.  
In this case, the style is read from right to left.  
The selector furthest to the right (`p`) is the *key selector*. It identifies exactly which element is being styled.  
Any selector to the left is a prequalifier.

When combining classes and ids with type selectors, there is no space between them.
```css
p.tiny {
  font-size: 0.2em;
}

span#first-time {
  color: red;
}
```

Classes and ids are separated when paired together
```css
.one .two {
  border: 1px solid black;
}

#one #two {
  background-color: #fff;
  } //This seems improper.
```

#### Pseudo-Classes and Pseudo-Elements
There are no spaces between selectors and pseudo-classes and pseudo-elements.

##### Pseudo-classes
###### For links
`:link` selects links that haven't been visited yet, while the mouse isn't hovering over or clicking it. 

`:visited` selects links that have been visited before, according to browser history.

`:hover` selects links that are being hovered on. Can be used other elements apart from links.

`:active` determines how a link looks as its being clicked. 

###### For others
`:focus` is similar to `:hover `. It applies when the visitor does something to indicate their attention to a web page, e.g clicking or tabbing.  
USeful for giving visitors feedback. Particularly useful with forms.

##### Pseudo-Elements
Syntax was changed from `:` to `::` but single colon still permitted for backward compatibility.

###### For paragraphs
`::first-letter`

`::first-line`

###### For others
`::before` lets you add content preceding an element.

`::after` adds generated content after an element.

`::selection` refers to elements that have been selected on a page.  
Can only set `color` and `background-color` with this pseudo-element.  
There is no single colon version of this pseudo-element.

`::first-child`

`::last-child`

`::nth-child` - More in child [pseudo-elements](##child-pseudo-elements)

`:first-of-type`

`:last-of-type`

`:nth-of-type`



### Attribute Selectors
```css
selector[attribute]

/*For elements with a particular attribute*/
a[title] {
  color: red;
}

/*For elements with a specific value for an attribute*/
a[href="..."] {
  color: red;
}

/*For elements with attributes that begin with a particular phrase. Doesn't work for secure connections*/
a[href^="http://"] {
  color: pink;
}

/*For elements with attributes that contain a particular phrase.*/
a[href*="image"]
```

### Child Selectors
A child is a tag that is directly nested in another tag.
```css
p > span {...}
```
#### Child Pseudo-elements

`::first-child`

`::last-child`

`::nth-child`
```css
/*Select alternating odd children elements*/
div:nth-child(odd)

/*Select alternating even children elements*/
div:nth-child(even)

/*Select every third element*/
div:nth-child(3n)

/*Select every fifth element starting from the second child element*/
div:nth-child(5n+2)
```
### SIbling Selector
Siblings are elements that come right after each other, not nested in each other.
```css
/*Adjacent Sibling*/
h1 + p {...}

/*General Siblings*/
h1 ~ p {...}
```
### The `:not()` selector
Called the negation pseudo-class.  
Used to exclude a tag from a general style.
```css
p:not(.sentence-one) {...}
```

1. Can't be used with descendant selectors, pseudo-elements, group selectors or combinators.


# Inheritance
Descendants inherit properties from ancestors.  

Doesn't just apply to tag styles. Also, class styles, ID styles, etc.

Some CSS properties are not inherited. Examples are `border`, `vertical-align`, `white-space`, `margin`, `padding`, etc.

# The Cascade
The cascade governs how styles interact and which styles get precedence when there's a conflict.

The cascade is a set of rules for determining which style properties get applied to an element. It specifies how a web browser should handle multiple styles when applied to the same tag and what to do when CSS properties conflict.

1. The last style applied to a tag based on its position on the style sheet is the one implemented. All styles cascade from the top of the style sheet to the bottom.
  ```css
  p {color:orange;}
  ...
  p {color:green;}
  /*The paragraph will be green*/
  ```

2. The most specific style is applied to the element
  ```css
  .paragraph {color:orange;}
  ...
  p {color:green;}
  /*The paragraph will be orange*/
  ```

# Specificity
Every selector has a specificity weight. A selector's specificity weight coupled with its placement in the cascade identifies how styles will be rendered.

In order of importance: 
**Inline Style - ID - Class - Type**

The higher the specificity weight of a selector, the more superiority it is given when a conflict occurs.

## Overriding Specificity
Using the `!important` tag
  ```css
  p {color:orange !important;} 
  ...
  p {color:green;}
  /*The paragraph will be orange*/
  ```

**Note**
1. `!important` only works on individual properties, not entire styles.
2. When two styles have `!important` tag, the more specific style wins.




# Colors

## Keyword Colors
These values are just the names of the colors you intend to use. Most common colors have keywords, and a few weird ones.  
Colors have to be part of CSS recommendations.

```css
p {
  color: black;
}
```

## Hexadecimal Color Notation
Oldest color system used by web designers.
Example: `#6600FF` contains three hexadecimal numbers.
`66` - represents red channel
`00` - represents green channel
`FF` - represents blue channel

The figures go from *0-9*, and the letters go from *a-f*. There are over 16.7 million hexadecimal colors.

The final color value is a blend of the amounts of red, green and blue specified.

```
#6600FF
#RRGGBB
```

Can be shortened to three characters if each set contains the same two numbers. Example:
```
#6600FF -----> #60F

#FFFFFF -----> #FFF
```


## RGB / RGBa
Color value consists of three numbers for each hue (red, green and blue).

The numbers can be from **0-255** or in percentages from **0-100**.
```css
p {
color: rgb(255,255,255); /*White*/
}

p {
color: rgb(100%, 100%, 100%); /*white*/
}
```

The *a* in RGBa stands for alpha. It controls transparency / level of opacity. It accepts values between 0 and 1.  
`0` is totally opaque, and `1` is invisible.
```css
p {
color: rgb(255,255,255,0.72); /*White*/
}

p {
color: rgb(100%, 100%, 100%, 0.5); /*white*/
}
```

## HSL / HSLa
```css
p {
  color: hsl(0, 100%, 50%); /*Bright red*/
}
```

HSL stands for hue, saturation and lightness/luminance. 

First value, *hue* is in degrees from *0-360*, which maps to a circle of hues. Think ROYGBIV.  
Each color is separated by around *51 degrees*. 
* red - 0, 360  
* yellow - around 50  
* orange - 100  
* green - 150, etc.

The second value is the *saturation*, or how pure the color is. Specified in percentages.
* 0% - dull gray (no matter the hue)
* 100% - pure colour (bright and vibrant)


The third value is the *lightness*, specified in percentages.
* 0% - completely black
* 100% - completely white
* 50% - pure colour


It also has an alpha channel, and supports opacity.
```css
p {
  color: hsla(0, 100%, 50%, 0.3); /*Bright red*/
}
```

# Measurement Values
These are the values used when indicating length, width or size in CSS.

## Absolute Units
Absolute units are best used for the print style sheets.

### Pixels
Essentially, a pixel in CSS is supposed to match to a pixel on a screen. That isn't necessarily the case.

Equal to 1/96 of an inch.

```css
div {
  border-width: 1px;
}
```

**Other absolute units include**
* `pt` - points; 1/72 inch
* `pc` - picas; equal to 12 points
* `mm`
* `cm`
* `in`

## Relative Units

### Keywords
`font-size: x-small;`

1. xx-small
2. x-small
3. small
4. medium: same as base size.
5. large
6. x-large
7. xx-large
8. larger
9. smaller

### Percentages
`font-size: 100%;`

Usually relative to the parent element OR base (font) size.
* 100% - base size

### Ems
In typography, `em` refers to the size of a capital *M* for a particular font.

In CSS, it is calculated based on element's font size.
**1 em = 100%**

For consistency, set body `width` to 100% when using ems. Mind the nesting.

**Other relative units include**
* `ex` - x-height; relative to height of lowercase *x*
* `ch` - zero width; equal to width of zero
* `vw` - viewport width unit
* `vh` - viewport height unit
* `vm` - viewport minimum unit
* `rem` - root em; relative to em size of root element (html)

**Note**: You can also use negative values.

# Formatting Text
A *typeface* is what we see; the artistic impression of how text looks, feels and reads.

A *font* is a file that contains a typeface.

## Font Types/Formats
1. **Embedded Open Type(EOT)**
Work only in Internet Explorer. 

2. **True Type(`.ttf` ** and **Open Type(`.otf`)**
Most commonly used formats. Has wide support in web browsers.  
Can also be used for word processing.

3. **Web Open Font Format `.woff`**
Designed specifically for the web. Basically compressed versions of `.ttf` and `.otf`.

Generally smaller in size and download quicker. Have wide browser support.

4. **Scalable Vector Graphic `.svg`**
Not actually a font format. Support for svg fonts is limited.  
File sizes are large. Only format understood by older Safari versions.

**Note**: A single font file contains just one weight and style. So each variation has to be downloaded if we're using web fonts.


## Properties
### The `font-family` property  
The `font-family` property specifies the font to be used.
```css
p {
  font-family: Arial;
}

p {
  font-family: "Helvetica Neue", Helvetica, Arial, sans-serif;
  /*The sans-serif is a generic font family. The browser gets to chose the actual font*/
}
```
To use a font, the visitor must have it installed on their computer. In case the font isn't present, fallbacks are created.  
The browser uses the first font it discovers the computer has.  
Font names consisting of two or more words have to be wrapped in quotation marks.

#### Generic font families
1. **Serif fonts**  
Best for long passages of text. It is believed that the 'serifs' gently lead the eye from letter to letter, making text easier to read.

Examples are Times New Roman, Times, Georgia.

2. **Sans-serif fonts**  
Used for headlines. Clean, simple appearance.

Examples are Arial, Helvetica, Verdana.


3. **Monospace fonts**  
Used to display computer code. Each letter is the same width. 


#### Using self-hosted fonts
Have to use the `@font-face` directive.
```css
@font-face {
  font-family: "League Gothic";
  src: url('fonts/League_Gothic_font.eot');
  src: url('fonts/League_Gothic_font.eot?#iefix') format('embedded-opentype'),/*For IE9 Compability Mode*/
  src: url('fonts/League_Gothic_font.woof') format('woff'),
  src: url('fonts/League_Gothic_font.ttf') format('truetype'),
  src: url('fonts/League_Gothic_font.svg') format('svg');
}

p {
  font-family: "League Gothic";
}
```

### The `color` property  
Changes the color of the text. Uses color values.  
*See [colors](#colors).*


### The `font-size` property  
Sets text size. Accepts measurement values.  
*See [measurement values](#measurement-values).*

Base text size should be 16px but to be on the safe side, set it to the root element or the body element.

For keywords, using 16px as base font size.

1. xx-small = 9px
2. x-small = 10px
3. small = 13px
4. medium: same as base font size.
5. large = 18px
6. x-large = 24px
7. xx-large = 32px
8. larger
9. smaller

### The `font-style` property  
```css
p {
font-style: normal/oblique/italic/inherit;
}
```

Oblique is identical to italic; also a slanted version of a font.  
The difference is:  
*Italic* is usually a separate typeface design with curved letter forms.  
**WHILE** *oblique* takes the normal font design and just slants it.

### The `font-weight` property  
Specifies if a font is bold or not, or the specific weight it should have.

1. **Keyword values** - normal, bold, bolder, lighter, inherit
2. **Numeric values** - 100-900 (normal - 400, bold - 700)

### The `font-variant` property
Switches types faces between variants.
1. `small-caps`
2. `inherit`
3. `normal`  

### The `text-transform` property
Change case of text  
1. `uppercase`
2. `lowercase`
3. `capitalize`
4. `none`
5. `inherit`

### The `text-decoration` property
![Text Decoration](img/css-text-decoration.png)
1. `underline`
2. `overline`
3. `line-through`
4. `blink` - makes text blink
5. `none`

You can combine multiple keywords for multiple effects
```css
text-decoration: underline overline;
```

### The `letter-spacing` and `word-spacing` property
Controls spacing between words and letters respectively.
Uses measurement values.
See *[measurement](#measurement-values)*

Note:  
Space between letters is called *tracking*.

### The `text-shadow` property
Lets you add drop shadows to text.
```css
text-shadow: horizontal-offset vertical-offset blur color;

text-shadow: -4px 4px 3px #999;
```

1. **Horizontal offset**  
How far to the left or right of the text the shadow should appear.
Negative values (-4px) make the shadow appear on the left, and positive values on the right.

2. **Vertical offset**  
How far above or below the text the shadow should appear.
Negative values make the shadow above the text, and positive values below.

3. **Blur**  
How blurry the shadow is.

### The `line-height` property
Adjust the space between lines. Uses *[measurement](#measurement-values)* values.

Percentage values are relative to `font-size`.

Normal `line-height` setting for a browser is 120%.

Note:  
To determine the amount of space that appears between lines of text, the browser subtracts the font size from the line height.  
The result - *leading* is the amount of space between lines in a paragraph.

You could also specify line height with just a number.
```css
line-height: 1.5;
```
The browser multiplied this number by the font size to determine the line height.

### The `text-align` property
Aligns text.

1. `left`
2. `right`
3. `justify`
4. `center`

### The `text-indent` property
Used to create a space between the text and the edge, to indicate a paragraph. Accepts *[measurement](#measurement-values)* values.

## The `font` shorthand
```css
font: style variant weight size/line-height font-family;

font: italic small-caps bold 14px/22px "Helevetica Neue", Helvetica, Arial, sans-serif;

/*Can omit some, but must include font-family and font-size*/
font: 14px "Helevetica Neue", Helvetica, Arial, sans-serif;

/*Font size must come before font family, at the end. The rest can be arranged in any order*/
font: italic bold small-caps 14px Arial;
font: bold small-caps italic 14px Arial;

/*Omitting a value form a list is the same as setting it to normal*/
font: 1.5em Arial; /*The other properties are set to normal and won't be inherited*/
```

# Styling Lists

## The `list-style-type` property
Decides the type of bullets for unordered lists, and the numbering scheme for ordered lists
**Bullets**
1. `disc`
2. `circle`
3. `square`

**Numbering Schemes**
1. `decimal`
2. `decimal-leading-zero`
3. `upper-alpha`
4. `lower-alpha`
5. `upper-roman`
6. `lower-roman`
7. `lower-greek`, etc.

![List Style Type](img/css-list-style-type.png)

## The `list-style-position` property
1. `inside`
2. `outside`

![List Style Position](img/css-list-style-position.png)

**Tip:**  
You can adjust the space between the bullet and text by increasing the `padding-left` property. Works only if `list-style-position` is set to `outside` or don't use it at all.

You could also use an image instead with the `list-style-image` property.


# Margins, Paddings and Borders

## The Box Model
![The Box Model](img/css-box-model.png)

**Padding**: The space between the content and the content's border.

**Border**: Line drawn around each edge of the box. Sits between the padding and margin.

**Margin**: Space that separates one element from another. This space is called a *gutter*.

### The `display` property
Determines how an element will be displayed
`inline` `inline-block` `block` `none`

### The `box-sizing` property
1. `content-box`
2. `border-box`

When set to `content-box`, the width and height values are applied to the content box. The padding, margin and borders are added on after that. This is the default value.

When set to `border-box`, the width and height values include the padding, margin and borders.

### The `width` and `height` property
Can only be specified for block-level elements and non-text inline elements.

*  `height`
*  `width`
*  `max-height`
*  `min-height`
*  `max-width`
*  `min-width`

### The `overflow` property
Specifies what to do when content doesn't fit
1. `visible`
2. `hidden`
3. `scroll`
4. `auto`
5. `inherit`

When set to `auto`, the browser decides. Usually scroll.

Accepts [measurement values](#measurement-values)

### The `box-shadow` property
Applied similarly to [`text-shadow`](#the-text-shadow-property) property. Optional values include:
```css
box-shadow: (inset) vertical-offset horizontal-offset shadow-radius (spread) shadow-color;

box-shadow: inset 4px 3px 2px 1px black;
```
The `inset` keyword tells a browser to draw the shadow inside the box.

The `spread` expands the shadow by the specified amount.

## Margins
Uses *[measurement](#measurement-values)* values.
```css
margin-right: 0px; /*Applies to all sides*/
margin-left: 0px;
margin-top: 0px;
margin-bottom: 0px;/*Don't need to add the px*/

/*Shorthand*/
margin: top right bottom left;
margin: top|bottom left|right;
margin: top left|right bottom;
```

### Collapsing Margins
When two margins collide, the browser applies the larger margin.  
To prevent this, use top or bottom padding instead or add a border.  
Left and right margins don't collapse.

## Padding
Uses *[measurement](#measurement-values)* values.
```css
padding-right: 0px; /*Applies to all sides*/
padding-left: 0px;
padding-top: 0px;
padding-bottom: 0px;/*Don't need to add the px*/

/*Shorthand*/
padding: top right bottom left;
padding: top|bottom left|right;
padding: top left|right bottom;
```

## Borders
Has three main properties; `border-color`, `border-width` and `border-style`.
```css
border: width style color;
border: 1px solid black;

border-top: 1px solid black;
border-bottom: 1px solid black;
border-left: 1px solid black;
border-right: 1px solid black;
```
The `border-width` property accepts
* Measurement values, except percentages.
* Keywords - `thin`, `medium` and `thick`.

The `border-style` controls the type of line drawn. Accepts keywords like
* `solid`
* `dotted`
* `dashed`
* `double`
* `groove`
* `ridge`
* `inset`
* `outset`
* `none`
* `hidden`  
* `inherit`
`None` and `hidden` work the same way; removing the border completely.
![Border Styles](img/css-border-style.png)

The `border-radius` property lets you curve the radius of the element. Applied similarly to padding and margin. Other applications include:
```css
border-radius: horizontal-radius/vertical-radius;
border-radius: top-left top-right bottom-right bottom-left;

border-radius: 40px/20px;
border-radius: 40px/20px 10px/30px 20px/40px 10px;
```
* `border-top-left-radius`
* `border-top-right-radius`
* `border-bottom-left-radius`
* `border-bottom-right-radius`

The `border-color` property sets the color for the border. 
`border-top-color` `border-right-color` `border-bottom-color` `border-left-color`
```css
border-color: top right bottom left;
```

THe `border-image` property lets you set an image as the border.
```css
border-image: image-source image-slice image-width image-outset image-repeat;

border-image: url(img.png) 33 33 33 33 stretch;
```
`border-image-slice` provides measurements to the four slice lines that divide the image into nine sections. The 33 numbers.  
`border-image-outset` specifies the distance for the image to hang out over the border.  
`border-image-repeat` specifies how the image should fill in the sides - stretch, round or repeat.


# The `float` property
Moves an element to the left or right. Content below the floated element wraps around it.

The element is removed from normal flow.
`left`  
`right`
`none`

## Clearing Floats `clear`
To prevent content from wrapping. The `clear` property is applied to the element after the floated element.

`left`  
`right` 
`both`  
`none`