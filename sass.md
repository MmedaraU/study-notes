- [References](#references)
- [Introduction](#introduction)
  - [Preprocessors](#preprocessors)
  - [About Sass](#about-sass)
  - [Output Styles](#output-styles)
- [Syntax](#syntax)
  - [Comments](#comments)
  - [Placeholder Selectors](#placeholder-selectors)
  - [Hidden Declarations](#hidden-declarations)
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
- [Imports](#imports)
  - [The `@import` directive](#the-import-directive)
    - [Import-only files](#import-only-files)
    - [Partials](#partials)
    - [Nested `@import`](#nested-import)
    - [Plain CSS Imports](#plain-css-imports)
  - [The `@use` directive](#the-use-directive)
  - [Choosing a Namespace](#choosing-a-namespace)
- [The `@extend` directive](#the-extend-directive)
- [Mixins](#mixins)
  - [The `@content` directive](#the-content-directive)
- [Mathematical Operations](#mathematical-operations)
- [Sass Functions](#sass-functions)
  - [User-Defined Functions](#user-defined-functions)
- [Built-in Modules](#built-in-modules)
  - [The `sass:math` module](#the-sassmath-module)
    - [Unit Functions](#unit-functions)
  - [The `sass:color` module](#the-sasscolor-module)
  - [The `sass:list` module](#the-sasslist-module)
  - [The `sass:map` module](#the-sassmap-module)
  - [The `sass:string` module](#the-sassstring-module)
- [Other Sass At-Rules](#other-sass-at-rules)
  - [The `@use` rule](#the-use-rule)
    - [Loading Members](#loading-members)
    - [Choosing a Namespace](#choosing-a-namespace-1)
    - [Private Members](#private-members)
  - [The `@forward` rule](#the-forward-rule)
    - [Adding a Prefix](#adding-a-prefix)
    - [Member Visibility](#member-visibility)
  - [The `@error` rule](#the-error-rule)
  - [The `@warn` rule](#the-warn-rule)
  - [The `@debug` rule](#the-debug-rule)
- [Changes to Note](#changes-to-note)
  - [Changes to CSS Variable Syntax](#changes-to-css-variable-syntax)

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


# Syntax
* Hyphens and underscores are used interchangeably.

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

## Hidden Declarations
Declarations that only show up some of the time. If a value is set to `null`, the declaration won't be compiled to CSS.
```scss
$rounded-corners: false;

.button {
  border: 1px solid black;
  border-radius: if($rounded-corners, 5px, null);
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

Units are also multipled when numbers are multiplied
```scss
4px * 2px //8px*px(square pixels)
5px / 2 //2.5px/s (pixels per second)
```

Operations can be carried out on similar units
```scss
1in + 6px //102px or 1.0625in
1in + 1s //Incompatible units
```

Percentages are treated differently from decimals e.g 0.5 and 50%.

Only the first ten digits of a number after the decimal point are included in the generated CSS.

Equality is considered up to the tenth digit after the decimal point.


## Colors
Ways of expressing a color are consistent with CSS - hsl, hsla, rgb, keywords, etc.


## Booleans
Coupled with conditional statements. `true` and `false`.  
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
Acts mostly as a container. Basically arrays; used to store a collection of related values, usually to iterate over them in order to perform a repeated action.

A Sass list is a collection of zero or more values separated by either spaces, commas or slashes(e.g font shorthand). Lists can be nested.

A list can contain zero elements. Indexing starts from 1.

```scss
$myList: (42, hotpink, 'kittens');
$myList: [10px 15px 0];
```
It's the delimiter (spaces or commas) that make the list, not the parentheses. The parentheses are optional unless the list is empty.

Lists are immutable - their content does not change. 

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
**Note: The `!global` flag can only be used to set a variable that has already been declared at the top level of the file.**

### The `!default` flag
Used to assign a value as the default for a variable if a value is not assigned. Particularly useful when creating libraries.
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

# Imports

## The `@import` directive
Sass and SCSS files imported using the SASS `@import` rules will be merged and output as a single file after compilation.

```scss
@import "main", "mobile"
```

The Sass `@import` rule has the ability to import Sass and CSS stylesheets, providing access to mixins, functions and variables.

Sass imports can't use interpolation but plain CSS imports can.

### Import-only files
Files that can be `imported` not `used`. 
`name.import.scss`

### Partials
Reusable chunks of code that you want to import but don't want to see in the final output. Handy for segregating the style code in various files for better organization.

The files are saved with an underscore `_` as the first character (e.g `_typography.scss`).

Partials are imported without the underscore `@import typography`.

### Nested `@import`
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

### Plain CSS Imports
Plain CSS imports (the files are downloaded) are triggered in Sass when
1. The file path of the imported files ends with a `.css` extension
2. The file path begins with `http(s)://`

You cannot import CSS directly into Sass except you change the file extension from `.css` to `.scss`

## The `@use` directive
Loads mixins, functions, and variables from other Sass stylesheets, and combines CSS from multiple stylesheets together. Stylesheets loaded by `@use` are called *modules*.

```scss
@use <url>

@use 'foundation/code'//code.scss file in the foundation folder
```
Any styles loaded with the `@use` rule will be included exactly once in the compiled CSS output, no matter how many times the styles are loaded.

The `@use` rules must come before any rules except `@forward`. Variables can be declared before the `@use` rule.

Modules loaded with `@use` are only visible in the stylesheet that loads them.
```scss
//src/_corners.scss
$radius: 3px;

@mixin rounded {
  border-radius: $radius;
}


//style.scss
@use "src/corners";

.button {
  @include corners.rounded;
  padding: 5px + corners.$radius;
}
```

## Choosing a Namespace
The default namespace for a module is the name without the extension.

**Choosing a different namespace for a module**
```scss
//style.scss
@use "src/corners" as c;

.button {
  @include c.rounded;
  padding: 5px + corners.$radius;
}
```

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

# Built-in Modules
These modules are loaded with the `@use` rule, and the functions are called like any other module member.

Built-in module URLs begin with `sass:` to indicate they're part of Sass itself.

```scss
@use "sass:color";

.button {
  $primary-color: #6b717f;
  color: $primary-color;
  border: 1px solid color.scale($primary-color, $lightness: 20%);
}
```

## The `sass:math` module
`math.$e` returns the value of the mathematical constant *e*;

`math.$pi` returns the value of the mathematical constant *pi*;

`math.ceil($number)` rounds the $number up to the next highest whole number
```scss
math.ceil(4); //4
math.ceil(4.2); //5
math.ceil(4.9); //5
```

`math.clamp($min, $number, $max)` restricts $number to the range between $min and $max. If $number is less than $min it returns $min, and if it's greater than $max it returns $max.

The units must be compatible or the numbers should be unitless.
```scss
math.clamp(-1, 0, 1); //0
math.clamp(1px -1px, 10px); //1px
math.clamp(-1in, 1cm, 10mm); //10mm
```

`math.floor($number)` rounds down to the nearest whole number.
```scss
math.floor(4); //4
math.floor(4.2); //4
math.floor(4.9); //4
```

`math.max($number)` returns the highest of one or more numbers.
```scss
math.max(1px, 4px); //4px

$widths: 50px, 30px, 100px;
math.max($widths...); //100px
```

`math.min($number)` returns the lowest of one or more numbers.
```scss
math.min(1px, 4px); //1px

$widths: 50px, 30px, 100px;
math.min($widths...); //30px
```

`math.round($number)` rounds $number to the nearest whole number.
```scss
math.round(4); //4
math.round(4.2); //4
math.round(4.9); //5
```

`math.abs($number)` returns the absolute value of the $number.

If the `$number` is negative, it returns `$number`, and if `$number` is +ve, it returns `$number`.
```scss
math.abs(10px); //10px
math.abs(-10px); //10px
```

`math.hypot($number)` returns the length of the n-dimensional vector that has components equal to each $number. For example, for three numbers a, b, and c, this returns the square root of a² + b² + c².  
The units must be compatible or the numbers should be unitless.
```scss
math.hypot(3, 4); //5

$lengths: 1in, 10cm, 50px;
math.hypot($lengths...); //4.0952775683in
```

`math.log($number, $base:null)` returns the logarithm of $number with respect to $base. If $base is null, the natural log is calculated.  
The $number and $base must be unitless.

```scss
math.log(10); //2.302585093
math.log(10, 10); //1
```

`math.pow($base, $exponent)` raises $base to the power of $exponent.  
The $base and $exponent must be unitless.

Trig functions include `math.sin` `math.cos` `math.tan` `math.acos` `math.asin` `math.atan` `math.atan2`

`math.div($number1, $number2)` returns the result of dividing number 1 by number 2.

`math.percentage()` converts a nuiless number to a percentage.

`math.random($limit: null)` returns a random number. If the limit is null, it returns a random number between 0 and 1. If limit is greater than or equal to 1, it returns a number between 1 and the limit.


### Unit Functions
`math.compatible($number1, $number2)` returns whether the numbers have compatible units.

`math.is-unitless` retuns whether number has no units.

`math.unit` returns unit of number.


## The `sass:color` module
`color.adjust()` is used to increase or decrease one or more properties of `$color` by fixed amounts.  
The red, blue and green arguments must be unitless, and range from -255 to 255.  
The hue argument must be in `deg` or unitless.  
The lightness, whiteness and blackness arguments must be between -100% and 100%, not unitless.  
The alpha argument must be between -1 and 1. 
```scss
color.adjust($color, $red: null, $green: null, $blue: null, $hue: null, $saturation: null, $lightness: null, whiteness: null, $blackness: null, $alpha: null)

@use "sass:color"
color.adjust(#6b717f, $red: 15); //#7a717f
```

`color.scale()` is used to fluidly scale a color's properties. Between -100% and 100%.
```scss
color.scale($color, $red: null, $green: null, $blue: null, $hue: null, $saturation: null, $lightness: null, whiteness: null, $blackness: null, $alpha: null)
```

`color.adjust()` is used to adjust a color's properties by fixed amounts.

`color.complement($color)` returns the RGB complement of $color.

`color.change()` is used to set a color's properties.
```scss
color.change($color, $red: null, $green: null, $blue: null, $hue: null, $saturation: null, $lightness: null, whiteness: null, $blackness: null, $alpha: null)
```

`color.blackness($color)` returns the HWB blackness of $color as a number between 0% and 100%. The RGB go from 0 to 255.

`color.complement($color)` returns the RGB complement of $color.

`darken($color, $amount)` makes $color darken by decreasing HSL lightness by set $amount; a number between 0 to 100%. Advisable to use `color.scale` instead.

`desaturate($color, $amount)` decreases HSL saturation of $color by a fixed $amount. Must be a number between 0 and 100%. Advisable to use `color.scale` instead.

`color.grayscale($color)` returns a gray color with the same lightness as `$color`. Identical to `color.change($color, $saturation: 0%)`

`color.hue($color)` returns hue of $color as a number between 0deg and 360deg.

`color.hwb($hue $whiteness $blackness / $alpha)` returns colors with given hue, whiteness, blackness and alpha.
```scss
color.hwb(210%, 0%, 60%); //#036
color.hwb(210% 0% 60% / 0.5); //rgba(0, 51, 102, 0.5)
```

`color.invert($color, $weight)` - Weight must be between 0 to 100%.

`lighten($color, $amount)` increases lightness by a fixed amount.

`color.mix($color1, $color2, $weight)` returns a mixture of both colors. A larger weight indicates more of color 1 should be used and vice versa.

## The `sass:list` module
***These functions can also be used with maps***

`list.append()` returns a list with a new item added to it.  
The separator can be a comma, space or slash. If set to `auto`, the separator used will be the one in the initial list.  
If the new value is a list, it is nested instead of all the items being added.  
Generally use to add single values to a list.
```scss
list.append($list, $val, $separator)
```

`list.index()` returns the idex of a value in a list. If the value isn't in the list, it returns `null`.  If the value occurs several times, it returns the index of its first appearance.
```scss
list.index($list, $value)
```

`list.is-bracketed($list)` returns whether a list has square brackets.

`list.join()` is used to the elements of two lists and returns a new list containing all items.  
If `$bracketed` is set to auto, the returned list will be bracketed if the first list is. Otherwise, it will be bracketed if truthy and not bracketed if falsey.
```scss
list.join($list, $separator, $bracketed);
```

`list.length($list)` returns the length of a list, or the number of pairs in a map.

`list.separator($list)` returns the name of the separator used by the list.

`list.nth($list, $n)` returns the element at the specified index. if `$n` is negative, it counts from the end of the list.

`list.set-nth($list, $n, $value)` replaces item at specified index with a new value.

`list.slash($elements)` returns a slash-separated lists that contains the elements.

`list.zip($lists)` combines every list in $lists into a single list of sub-lists.  
Each element in the returned list contains all the elements at that position in $lists.  
The returned list is as long as the shortest list in $lists.  
The returned list is always comma-separated and the sub-lists are always space-
separated.  
```scss
list.zip(10px 50px 100px, short mid long); // 10px short, 50px
mid, 100px long
list.zip(10px 50px 100px, short mid); // 10px short, 50px mid
```

## The `sass:map` module

## The `sass:string` module
`string.quote` returns a string as a quoted string.

`string.index($string, $substring)` returns index of substring in string, or null if it isn't there.
```scss
string.index("Helevetica Neue", "Helvetica"); /1
string.index("Helevetica Neue", "Neue"); /11
```

`string.insert($string, $insert, $index)` inserts new value at specified index in string. If the index is higher than the length of the string, it is added at the end. If its smaller than the negative length, the value is added to the beginning.
```scss
string.insert("Roboto Bold", " Mono", 7); //Roboto Mono Bold
string.insert("Roboto Bold", " Mono", -6); //Roboto Mono Bold
```

`string.length` returns the number of characters in a string, including the spaces.

`string.slice($string, $start-at, $end-at: -1)` returns the slice of string starting at the specified index.

`string.to-upper-case` and `string.to-lower-case` return string in uppercase and lowercase respectively.

`string.unique-id` returns a unique id guaranteed to be a valid CSS identifier and valid within the current Sass configuratiion.

`string.unquote` returns unquoted strings. The produced strings are not valid CSS.

# Other Sass At-Rules

## The `@use` rule
The `@use` rule loads mixins, functions and variables from other Sass stylesheets, and combines CSS from multiple stylesheets together.

Stylesheets loaded with `@use` are called modules. Any styles loaded this way are used exactly once in the compiled CSS no matter how many times they are loaded.
```scss
// foundation/_code.scss
// foundation/_lists.scss


@use 'foundation/code';
@use 'foundation/lists';
```

The `@use` rule only makes members available within the scope of the current file. It never adds them to the global scope.

The `@use` rule loads each file once. It must appear at the beginning of the file and cannot be nested in style rules.

Each `@use` rule can only have only one URL and requires quotes around its URL even when using the indented syntax.

### Loading Members
You can access variables, functions, and mixins from imported modules.  

Members loaded with `@use` are only visible in the stylesheet that loads them.

If you want to load members from many files at once, you can use the `@forward` rule to forward them all from one shared file.

`@use` adds namespaces to member names.
```scss
<namespace>.<variable>
<namespace>.<function>
@include <namespace>.<mixin>

// src/_corners.scss
$radius: 3px;
@mixin rounded {
  border-radius: $radius;
}


//style.scss
@use "src/corners";
.button {
  @include corners.rounded;
  padding: 5px + corners.$radius;
}
```

### Choosing a Namespace
By default, a namespace is the last component of a module's URL without a file extension. It can be changed though.
```scss
<namespace>.<variable>
<namespace>.<function>
@include <namespace>.<mixin>

// src/_corners.scss
$radius: 3px;
@mixin rounded {
  border-radius: $radius;
}


//style.scss
@use "src/corners" as c;
.button {
  @include c.rounded;
  padding: 5px + c.$radius;
}
```

A module can be loaded without a namespace by writing `@use "<url>" as *`.
```scss
// src/_corners.scss
$radius: 3px;
@mixin rounded {
  border-radius: $radius;
}


//style.scss
@use "src/corners" as *;
.button {
  @include rounded;
  padding: 5px + $radius;
}
```

### Private Members
Members (variables, mixins, etc) of a stylesheet that are made to not be available outside that stylesheet.
```scss
$-radius: 3px; //Throws an error when used in another stylesheet
```

To make a member private to an entire package rather than a single module, don't forward the module or the member can be hidden.

## The `@forward` rule
The `@forward` rule loads a stylesheet and makes its members available when the stylesheet is loaded with the `@use` rule.

The `@forward` rule makes the public members of the loaded module available to
users of your module as though they were defined directly in your module. Those members
arenʼt available in your module. If you want that, youʼll need to write a `@use` rule
as well.

If you do write both a `@forward` and a `@use` for the same module in the same file, itʼs
always a good idea to write the `@forward` first.

```scss
// src/_list.scss
@mixin list-reset {
  margin: 0;
  padding: 0;
  list-style-type: none;
}

// bootstrap.scss
@forward "src/list";

//styles.scss
@use "bootstrap";

li {
  @include bootstrap.list-reset;
}
```

### Adding a Prefix
```scss
// src/_list.scss
@mixin reset {
  margin: 0;
  padding: 0;
  list-style-type: none;
}

// bootstrap.scss
@forward "src/list" as list-*;

//styles.scss
@use "bootstrap";
li {
  @include bootstrap
}
```

### Member Visibility
```scss
// src/_list.scss
$horizontal-list-gap: 2em;

@mixin list-reset {
  margin: 0;
  padding: 0;
  list-style-type: none;
}

@mixin list-horizontal {
  @include list-reset;

  li {
    display: inline-block;
    margin: {
      left: -2px;
      right: $horizontal-list-gap;
    }
  }
}

// bootstrap.scss
@forward "src/list" hide list-reset, $horizontal-list-gap;
//OR
@forward "src/list" show list-reset, $horizontal-list-gap;
```

## The `@error` rule
Lets compilation fail with an error message
```scss
@mixin reflexive-position($property, $value) {
@if $property != left and $property != right {
@error "Property #{$property} must be either left or right.";
}


$left-value: if($property == right, initial, $value);
$right-value: if($property == right, $value, initial);


left: $left-value;
right: $right-value;
[dir=rtl] & {
left: $right-value;
right: $left-value;
}
}


.sidebar {
@include reflexive-position(top, 12px);
// ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
// Error: Property top must be either left or right.
}
```

## The `@warn` rule
Prints a warning without stopping compilation entirely.
```scss
$known-prefixes: webkit, moz, ms, o;

@mixin prefix($property, $value, $prefixes) {
@each $prefix in $prefixes {
@if not index($known-prefixes, $prefix) {
@warn "Unknown prefix #{$prefix}.";
}

-#{$prefix}-#{$property}: $value;
}
#{$property}: $value;
}


.tilt {
// Oops, we typo'd "webkit" as "wekbit"!
@include prefix(transform, rotate(15deg), wekbit ms);
}
```

## The `@debug` rule
Prints a message for debugging purposes
```scss
@mixin inset-divider-offset($offset, $padding) {
$divider-offset: (2 * $padding) + $offset;
@debug "divider offset: #{$divider-offset}";

margin-left: $divider-offset;
width: calc(100% - #{$divider-offset});
}
```

# Changes to Note
* Can't extend compound selectors

## Changes to CSS Variable Syntax
```scss
$accent-color: #fbbc04;

:root {
// WRONG, will not work in recent Sass versions.

--accent-color-wrong: $accent-color;
// RIGHT, will work in all Sass versions.
--accent-color-right: #{$accent-color};
}
```
Because interpolation removes quotation marks from quoted strings, it may be
necessary to wrap them in the meta.inspect() function to preserve their quotes.
```scss
@use "sass:meta";

$font-family-monospace: Menlo, Consolas, "Courier New", monospace;

:root {
--font-family-monospace: #{meta.inspect($font-family-monospace)};
}
```