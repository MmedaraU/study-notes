- [References](#references)
- [Introduction](#introduction)
  - [Preprocessors](#preprocessors)
  - [About Sass](#about-sass)
  - [Output Styles](#output-styles)
- [Basic Syntax Rules](#basic-syntax-rules)
  - [Comments](#comments)
  - [Placeholder Selectors](#placeholder-selectors)
- [Data Types](#data-types)
  - [Strings](#strings)
  - [Numbers](#numbers)
    - [How Units are handled in Sass](#how-units-are-handled-in-sass)
  - [Colors](#colors)
  - [Booleans](#booleans)
  - [Null](#null)
  - [Lists](#lists)
  - [Maps](#maps)
- [Nesting](#nesting)
  - [Selector Nesting](#selector-nesting)
  - [Property Nesting](#property-nesting)
  - [Context Nesting](#context-nesting)
  - [Referencing a Parent Selector](#referencing-a-parent-selector)
  - [The `@at-root` directive](#the-at-root-directive)
- [Variables](#variables)
  - [Scope](#scope)
    - [The `!global` flag](#the-global-flag)
    - [The `!default` flag](#the-default-flag)
- [Interpolation](#interpolation)
- [Loops and Conditions](#loops-and-conditions)
  - [The `@if` directive](#the-if-directive)
  - [The `@for` loop](#the-for-loop)
  - [The `@each` loop](#the-each-loop)
  - [The `@while` loop](#the-while-loop)
- [The `@import` directive](#the-import-directive)
  - [Partials](#partials)
  - [Nested `@import`](#nested-import)
  - [Plain CSS Imports](#plain-css-imports)
- [The `@extend` directive](#the-extend-directive)
- [Mixins](#mixins)
  - [The `@content` directive](#the-content-directive)
- [Mathematical Operations](#mathematical-operations)
- [Sass Functions](#sass-functions)
  - [User-Defined Functions](#user-defined-functions)
  - [Native Functions](#native-functions)
    - [Numeric Functions](#numeric-functions)
    - [Color Functions](#color-functions)
    - [List Functions](#list-functions)

# References
> **Beginning CSS Preprocessors** with Sass, Compass, and Less by *Anirudh Prabhu*. (Sass v3.3.5)
> 
> **Jump Start Sass** by *Hugo Giraudel and Miriam Suzanne*
> 
> **[Sass Documentation for Dart Sass 1.53.0 and LibSass 3.6.5](https://sass-lang.com/documentation)**

# Introduction

## Preprocessors
A preprocessor takes one form of data and converts it to another. Sass is a preprocessor language.

CSS uses a declarative form of programming - styles are used directly by browser without compiling.

## About Sass
Sass stands for *Syntactically Awesome Stylesheets*. It was designed and developed by Hampton Caitlin and Natalie Weizenbaum.

Sass is a preprocessor language that is an extension of CSS.

The Sass preprocessor allows two syntaxes
1. Sass (indented syntax)
2. SCSS or Sassy CSS; a CSS-like syntax

The *Sass/indented syntax* uses a Ruby-like syntax with no braces or semicolons, and a strict indentation. This syntax is white-space sensitive.
```sass
.media
  margin: 10px
  overflow: hidden
```

The *.scss format* adheres closely to the CSS syntax. If it's valid CSS, it's valid SCSS.
```scss
.media {
  margin: 10px;
  overflow: hidden;
}
```

## Output Styles
How Sass outputs CSS - *nested, expanded, compact, compressed*. The amount of space they consume reduces with each style.

1. **nested**  
    Default output style - shows CSS in normal format. Indentation is per nesting in original Sass document.
    ```scss
    .container {
      color: #000; }

    .container p {
      padding: 10px; }
    ```

2. **expanded**  
    The output is derived as if CSS were handwritten. 
    ```scss
    .container {
      color: #000;
    }

    .container p {
      padding: 10px;
    }
    ```

3. **compact**  
    Consumes less space than the previous styles. Puts all properties on a single line, with one rule per line.
    ```scss
    .container {color: #000;}

    .container p {padding: 10px;}
    ```

4. **compressed**  
    Takes less space than all the output styles. It eliminates all white space.
    ```scss
    .container {color: #000;}.container p{padding: 10px;}
    ```


# Basic Syntax Rules
Hyphens and underscores are used interchangeably.

## Comments
```scss
// This is a single line comment

/* This is a multi line comment*/
```
When the Sass file is compiled, multi-line comments are retained while single-line comments are removed.



## Placeholder Selectors
Selectors that are not rendered in the final `.css` file. Used to extend certain sets of styles without rendering i]that set in the final output.
```scss
//Placeholder Selector
%importantText {
  color: red;
  font-weight: bold;
}

.notice {
  @extend %importantText;
}

//Translates to
.notice {
  color: red;
  font-weight: bold;
}
```

# Data Types
1. Numbers - *e.g 42, 130px*

2. Strings - *e.g "Hello world", kittens*

3. Colors - *e.g red, #bada55*

4. Boolean - *true or false*

5. List - *e.g (a, b, c), a b c*

6. map - *e.g (a:1, b:2)*

7. null

Math functions can be performed on numbers and colors, but not strings. Some functions can be performed on lists and maps, but not on booleans and null values.

## Strings
A string is a series of characters. They do not  need to be quoted in Sass, as long as non-identifier characters are escaped.

A quoted string is strictly equivalent to its quoted counterpart. Quoting strings is however a good practice.

```scss
//Concatenating Strings
$base-path: '/images/';
$file-name: '/kittens';
$extension: 'png';

$file-path: $base-path + $file-name + '.' + $extension; //'images/kittens.png'
```

## Numbers
A number in Sass can have a unit.

You can perform operations on numerical values - add(+), subtract(-), multiply(\*), divide(/), modulo(%). Check *[Mathematical Operations](#mathematical-operations)*.

The slash symbol (/) apart from division, has other uses e.g in the font shorthand property. There are three scenarios in which Sass does perform division instead of leaving the slash;

1. If the value, or any part of it, is stored in a variable or returned by a function.
2. If the value is surrounded by parentheses. `e.g (16px/2)`
3. If the value is used as part of another arithmetic expression. `e.g width: 300px + 16px / 2;`


### How Units are handled in Sass
Units are not just strings attached to a number, they are part of the number.
```scss
$value: 42;
$good: $value * 1px; //42px --> number
$bad: $value + px; //'42px' --> string
```

## Colors
Ways of expressing a color are consistent with CSS - hsl, hsla, rgb, keywords, etc.


## Booleans
Coupled with conditional statements.
*Instead of a `!` symbol, Sass has a `not` keyword.*

## Null
Null is both the value and the data type. It is commonly used to describe an empty value that will be filled later on, or an empty state that's neither true or false. Sass omits a declaration with a null data type altogether.

Especially useful for building mixins.
```scss
@mixin absolute($top: null, $right: null, $bottom:null, $left:null) {
  position: absolute;
  top: $top;
  right: $right;
  bottom: $bottom;
  left: $left;
}

//Example
.foo {
  @include absolute($top: 13px, $left: 37px);
}
```

## Lists
Acts mostly as a container. BAsically arrays; used to store a collection of related values, usually to iterate over them in order to perform a repeated action.

A Sass list is a collection of zero or more values separated by either spaces or commas. Lists can be nested.

```scss
$myList: (42, hotpink, 'kittens');
```
It's the delimiter (spaces or commas) that make the list, not the parentheses. The parentheses are optional unless the list is empty.

## Maps
Similar to lists.

A map is a series of pairs of associated keys and values where keys are unique to each map. 

Lists are tied to a specific order, while maps are located by their key.

Keys of a map can be of any type.

```scss
$message-themes: (
  'info': deepskyblue,
  'danger': tomato,
  'warning': gold,
  'confirm': lightgreen,
);

.message-info {
  color: map-get($message-themes, 'info');
}
.message-danger {
  color: map-get($message-danger, 'danger');
}
.message-warning {
  color: map-get($message-warning, 'warning');
}
.message-confirm {
  color: map-get($message-confirm, 'confirm');
}
```

# Nesting

## Selector Nesting
```scss
.article {
h1 {
  font-weight: bold;
}

p {
  line-height: 1em;
}

img {
  float: left;
}
}
```

## Property Nesting
```scss
.content {
  font: {
    family: 'Tahoma';
    size: 13px;
    weight: bold;
  }
}
```

Media queries can be nested in style rules
```scss
.container {
  width: 960px;

  @media screen and (min-width: 500px){
    width: 100%;
  }
}
```

## Context Nesting
* Nesting media queries in style rules
```scss
div {
  display: block;

  @media screen and (min-width: 42em) {
    display: inline-block;
  }
}
```

* Nesting media queries
```scss 
@media screen {
  div {
    display: block;

    @media (min-width: 42em) {
      display: inline-block;
    }
  }
}
```

## Referencing a Parent Selector
When nesting styles, the ampersand `&` sign can be used to reference the parent selector regardless of the level of nesting.
```css
a {
  text-decoration: none;

  &:hover {/*Translates to `a:hover`*/
    text-decoration: underline;
  }
}
```

## The `@at-root` directive
Causes the rules inside it to be rendered at the document root level regardless of where they are nested.

It is used within selectors.

```scss
.notification {
  border-radius: 5px;
  padding: 5px;
}

.errorLooks {
  @extend .notification;

  @at-root {
    .icon {
      border-radius: 50%;
    }
  }
}

//Output
.notification, .errorLooks {
  border-radius: 5px;
  padding: 5px;
}

.icon {
  border-radius: 50%;
}
```
The content of the `@at-root` directive will appear after the rules within which it was nested.

# Variables
It is a storage location paired with an associated identifier(variable name). Made up of a key and a value.

Used to store values to a name that is available to reuse across the code. Can be reused throughout the stylesheet.

```scss
$fontColor: #666; //Variable

body {
  color: $fontColor;
}
```

When compiled, the variable used in the style is replaced with the actual value.

Variables when declared outside any style declaration, are globally accessible.

When specified inside a specific selector, they will be available only to that selector.

It is possible to create a variable form another variable.
```scss
$borderColor: #000;
$borderDeclaration: 2px $borderColor solid;
```

Variables can be given default values that will come into action if they are not assigned any specific value (within a selector).
`$borderRadius: 5px !default;`

**Note: To know what data type a variable is, we use the `type-of() function.**

## Scope
Variables can be defined anywhere in a stylesheet.
However, the access of a variable may be restricted based on where it is assigned.

Variables defined in a mixin, function or rule set are *local* by default. Global variables are defined outside rule sets or at the root element.

Global and local variables can share the same name - this is known as *variable shadowing*. The local variable is said to shadow the global one with the same name.

### The `!global` flag
To make a local variable a global one, the `!global` flag is used.
```scss
$padding: 10px;

.module {
  $padding: 20px !global;
  padding: $padding; //20px
}

.foo {
  padding: $padding; //10px
}
```

### The `!default` flag
Used to assign a value as the default for a variable if a value is not assigned.
```scss
$padding: 10px;
$padding: 20px !default;

.foo {
  padding: $padding; //10px
}
```

# Interpolation
The process of evaluating an expression or a string containing one or more variables, yielding a result in which the variables are replaced with their corresponding values in memory.

For building selectors or properties dynamically; comes handy when you want to use loops to generate styles. 
```scss
$innerContainerClass: container;

.left .#{$innerContainerClass} {
  width: 50%;
  display: inline-block;
}

//Translates to
.left .container {
  width: 50%;
  display: inline-block;
}
```

Can also be used for concatenating strings or in calculations and in other ways
```scss
//Instead of this
$name: 'Hugo';

.foo {
  content: 'Hello' + $name + '!'; //Hello Hugo!
}

//Interpolation does this
$name: 'Hugo';

.foo {
  content: 'Hello #{$name}!'; //Hello Hugo!
}
```



# Loops and Conditions
Used to include styles or bringing some variation in styles based on some condition. Commonly used in mixins.

## The `@if` directive
Takes an expression and applies the associated style if the expression evaluates to something other than false or null.
```scss
// Just @if directive
$isVisible: true !default;

.container {
  @if $isVisible {
    display: block;
  }
  @else {
    display: none;
  }
}

//Combining @if, @else if and @else
$blockColor: green;
.container {
  @if $blockColor == red {
    background-color: #f00;
  } @else if $blockColor == green {
    background-color: #0f0;
  } @else if $blockColor == blue {
    background-color: #00f;
  } @else {
    background-color: #000;
  }
}
```

Using the `and` and `or` keywords
```scss
@if true and false {
  //Write statement
}
@if true or false {
  //Write statement
}
```

## The `@for` loop
Used to output styles by means of looping. You can adjust styles based on the value of the counter.
```scss
//Variation 1
@for $size from 1 through 3 {//Counts to 3
  .header-#{$size} {
    font-size: 2em * $size;
  }
}

//Variation 2
@for $size from 1 to 3 {//COunts to 2
  .header-#{$size} {
    font-size: 2em * $size;
  }
}
```

## The `@each` loop
A looping directive that uses a list instead of counters.
```scss
$socials: twitter linkedin pinterest;

@each $social in $socials {
  .#{social} {
    background-image: url(/images/icons/#{$social}.png);
    width: 16px;
    height: 16px;
  }
}

//Number 1 Translation
  .twitter {
    background-image: url(/images/icons/twitter.png);
    width: 16px;
    height: 16px;
  }
```

```scss
@each $notification, $color in (success, green), (warning, amber), (error, red) {
  .#{$notification}-icon {
    background-color: $color;
  }
}

//Translation 1
.success-icon {
  background-color: green;
}
```

## The `@while` loop
Iterates until the condition is not met and outputs the styles nested inside the loop.

```scss
$col: 4;
@while $col > 0 {
  .cols-#{#col} {
    width: 100% / $col;
  }
  $col: $col -1;

//Translates to
.cols-4 {
  width: 25%;
}
.cols-3 {
  width: 33.3333%;
}
.cols-2 {
  width: 50%;
}
.cols-1 {
  width: 100%;
}
}
```

# The `@import` directive
Sass and SCSS files imported using the SASS `@import` rules will be merged and output as a single file after compilation.

```scss
@import "main", "mobile"
```

## Partials
Reusable chunks of code that you want to import but don't want to see in the final output. Handy for segregating the style code in various files for better organization.

The files are saved with an underscore `_` as the first character (e.g `_typography.scss`).

Partials are imported without the underscore `@import typography`.

## Nested `@import`
Importing code snippets within style rules
```scss
//_parent.scss
.parent {
  background-color: #ccc;
}

//styles.scss
.child {
  @import "parent";
}


//Output
.child .parent {
  background-color: #ccc;
}
```

## Plain CSS Imports
Plain CSS imports (the files are downloaded) are triggered in Sass when
1. The file path of the imported files ends with a `.css` extension
2. The file path begins with `http(s)://`

You cannot import CSS directly into Sass except you change the file extension from `.css` to `.scss`

# The `@extend` directive
This is known as selector inheritance - inheriting the styles defined in another selector.

```scss
.notification {
  border-radius: 5px;
  padding: 5px;
}

.success {
  @extend .notification;
  background-color: #0f0;
}

//Output
.notification, .success {
  border-radius: 5px;
  padding: 5px;
}

.success {
  background-color: #0f0;
}
```

The `@extend` directive cannot be used in media queries. It cannot accept arguments like mixins.

You could also extend [placeholder selectors](#placeholder-selectors).

**Note: `@extend` does not work across media queries.**

# Mixins
Mixins are functions that can output code rather than return a result.

Used to create reusable style code that can be used across the entire stylesheet. They can contain full CSS rules and can take arguments.

```scss
@mixin roundedEdges($radius:5px) {
  //5px is the default incase an argument is not specified
  -webkit-border-radius: $radius;
  -moz-border-radius: $radius;
  -ms-border-radius: $radius;
  border-radius: $radius;
}

.container {
  @include roundedEdges(10px);
}

//Output
.container {
  -webkit-border-radius: 10px;
  -moz-border-radius: 10px;
  -ms-border-radius: 10px;
  border-radius: 10px;
}
```

You can pass a block of code as an argument
```scss
@mixin clearfix {
  &:after 
  {
    @content;//Use content of selector mixin is placed in
  }
}

.btn {
  display: inline-block;
  @include clearfix {
    clear: both;
  }
}

//Output
.btn {
  display: inline-block;
}

.btn:after {
  clear: both;
}
```

Several variables can be used as arguments in mixins
```scss
@mixin fancyBorder($fbColor:#fff, $fbWidth:3px)
//Default values can be set for arguments
{
border-color: $fbColor;
border-width: $fbWidth;
border-style: dashed;
}

.specialNote {
  @include fancyBorder(#000, 2px)
}
```

## The `@content` directive
This directive is specific to mixins. Lets the style rule pass code to the mixin instead of the mixin having default styles.

```scss
@mixin on-event {
  &:hover, &:active. &:focus {
    @content;
  }
}

.foo {
  color: blue;

  @include on-event {
    color: red;
  }
}
```

# Mathematical Operations
1. Addition
    ```scss
    .container {
      width: 20%+80%;
    }
    ```

2. Subtraction
    ```scss
    .container {
      width: 80%-20%;
    }
    ```

3. Multiplication
    ```scss
    .container {
      width: 20%*4;
    }
    ```

4. Division
    ```scss
    .container {
      width: 80%/4;
    }
    ```

5. Parentheses
Used to manipulate the order of execution
```scss
.leftSide {
  font-size: 1em + (.2em*2); //1.4em
}
```

# Sass Functions
Math functions can be performed on numbers and colors, but not strings. Some functions can be performed on lists and maps, but not on booleans and null values.

## User-Defined Functions
Functions are chunks of code that return a result, possibly accepting arguments.

Uses the `@function` directive. It returns a result. Similar to JS functions.

The `@return` directive similar to `return` in JS. Accepts Sass expressions, processes them and returns the result.

The function stops after `@return` is triggered.

```scss
@function generateGrid($columns) {
  @return percentage(1/$columns);
}

.two-column {
  width:generateGrid(2);
}

//Output
.two-column {
  width: 50%;
}
```

## Native Functions

### Numeric Functions
1. **abs(number)**  
    Returns an absolute value of the number.
    ```scss
    abs(1.1em) //1.1em`
    ```

2. **ceil(number)**  
    Provides a rounded-up value of a number
    ```scss
    ceil(1.1em) //2em
    ```

3. **floor(number)**  
    Returns a rounded-down value of a number.
    ```scss
    floor(1.1em) //1em
    ```

4. **percentage(number)**  
    Converts the provided number into a percentage
    ```scss
    percentage(1.1) //110%
    ```

5. **round(number)**  
    Return the nearest round value of the number provided
    ```scss
    round(1.1em) //1em
    ```

### Color Functions
Functions for transforming colors

1. **adjust_color(color, number)**  
    Assigns individual properties of colours. The number values can be negative or positive.  
    The properties that can be transformed are
    * red
    * green
    * blue
    * hue
    * lightness
    * alpha
  
    ```scss
    adjust_color(#000, $red:-5);
    ```

2. **complement(color)**  
    Returns the complement of the color
    ```scss
    complement(#ff0000); //cyan
    ```

3. **grayscale(color)**  
    Returns the grayscale version of a color

### List Functions
Sass lists start counting from 1.

1. **nth(list, index-number)**  
    Used to fetch a single item from a list.
    ```scss
    nth(10px 20px 30px, 1)//10px
    ```

2. **join(list1, list2, [separator])**  
    Used to generate a new list by combining two lists.  
    Each value in the list counts as a single item.  
    This function can also be used to make list out of individual items.  
    The `separator` is optional, and can be a space or a comma. The default is the separator used in list 1.

3. **length(list)**  
    Returns the number of items in a list.
    ```scss
    length(10 22 33) //3
    ```