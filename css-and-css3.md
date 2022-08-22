# References
> Learn to Code HTML and CSS: Develop and Style Websites by Shay Howe 
>  
> 


# Introduction
CSS stands for *Cascading Style Sheets*. It is a presentation language created to style the appearance of content.

## Common CSS Terms
1. **Selectors**: A selector designates exactly which element or elements within our HTML to target and apply styles to. Selectors can target an id, class or a type of element.

2. **Properties**: Determines the styles that will be applied to the element targeted. Examples include `color`, `width`, etc.

3. **Values**: A value determines the behaviour of a property. 

### How they are used
```css
p {
  color: orange;
}
```
* `p` - selector
* `color` - property
* `orange` - value
* `p {...}` - rule set
* `color: orange;` - declaration

## Referencing CSS
1. Inline
2. Internal
3. **External style sheet**: Done by linking an external CSS file (a plain text file with a .css file extension). This file should be saved within the same folder, or a subfolder, where the HTML is located.
   Here's how an external style sheet is linked
   ```html
    <head>
      <link rel="stylesheet" href="main.css">
    </head>
   ```

## CSS Resets
Every web browser has its own default styles for different styles. CSS Resets are used to ensure cross-browser compatibility.

CSS Resets take every common HTML elements and provides a unified styles for browsers. Resets generally involve removing any sizing. margins, paddings, etc and toning these values down.


# Selectors

## Type Selectors
Targets selectors by their element type.
```html
<div>...</div>
```
```css
div {...}
```

## Class Selectors
Targets an element based on the class attribute. They are more specific than type selectors - select a particular group of elements rather than all elements of one type.
```html
<div class="awesome">...</div>
```
```css
.awesome {...}
```

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
