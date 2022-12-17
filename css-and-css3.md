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

# References
> **Learn to Code HTML and CSS: Develop and Style Websites** by *Shay Howe*  
> 
> **CSS3: The Missing Manual** by *David Sawyer McFarland*
> 


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
    <h1 style="color:#666"></h1>
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