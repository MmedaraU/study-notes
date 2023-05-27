

# References
> **Jump Start Bootstrap** by *Syed Fazle Rahman*
> 
> **The Joy of Bootstrap** by *Alan Forbes*


# Introduction v.3
Bootstrap is a front-end framework that helps develops to jump start the web development process.

It was developed in 2011 by Mark Otto and Jack Thornton.

# The Bootstrap Grid System
```html
  <section class="container">
    <div class="row">
      ...
    </div>
  </section>
```
A grid system allows us to properly house our website's content. It divides the screen into multiple rows and columns that can be used to create various types of layouts.

The Bootstrap grid system divides the screen into columns - up to 12 in each row.

Rows and columns have to be placed inside a container to ensure proper alignment and padding. There are two container classes - `container` and `container-fluid`.

`container` creates a fixed-width container which appears at the center of the screen with space on both sides

`container-fluid` creates a full-width container that fills up the screen.

`col-xs` for extra small displays  
`col-sm` for smaller displays  
`col-md` for medium displays  
`col-lg` dor larger displays

For example, `col-xs-12` means an element should span 12 columns for extra small displays

## Nesting Columns
```html
  <section class="container">
    <div class="row">

      <div class="col-md-6 col-1">
        
        <div class="row">
          <div class="col-md-6"></div>
          <div class="col-md-6"></div>
        </div>

      </div>
      <div class="col-md-6 col-2"></div>
    </div>
  </section>
```

## Offsetting Columns
Used to increase the left margin of a column
`col-xs-offset`  
`col-sm-offset`  
`col-md-offset`  
`col-lg-offset`

```html
<!--Works for centering columns-->
<div class="row">
      <div class="col-xs-6 col-xs-offset-3 col-1">
        <h1>Hello World</h1>
      </div>
    </div>
```

## Reordering Grids
The `pull` classes move columns towards the left by a certain number of columns

The `push` classes move columns towards the right by a certain number of columns

`col-**-pull-[no.]`  
`col-**-push-[no.]`  

# Page Components
* Headers
* Panels
* Media Object
* Thumbnails
* List Group
* Navigation
* Breadcrumb
* Labels
* Buttons
* Wells
* Badges
* Forms
* Carousels
* Pagination
* Progress bars


## Contextual Classes
Used to gives rows `context`, make them stand out based on some contextual reason
`.active` applies the hover color

`.success` indicates a successful or positive action. Uses a **green** color

`info` indicates a neutral info change or action. Uses a **sky blue** color

`warning` indicates a warning that might need attention. Uses a **yellow** color

`danger` indicates a dangerous or potentially negative action. Uses a **red** color

`primary` uses a **deep blue** color

Contextual colors can be used in several ways and with several elements
```
bg-
text-
```

## Typography
Headings `<h1>` to `<h6>` are automatically styled in Bootstrap.

Blockquotes are styled using the `blockquote` class.

`text-muted` gives the text a gray color. Other contextual colors can also be used.

## Buttons
Add a `btn` class to an anchor `a` element

`btn-default`  `btn-link`  `btn-success`  `btn-info`  `btn-warning`  `btn-danger`  `btn-link`  

`btn-lg` `btn-sm` `btn-xs`  
`btn-block` creates block-level buttons; they span the full width of a parent.


## Navigation
Bootstrap navbars are responsive.

## Tables
Has to have the `table` class

`table-striped` adds zebra-striping to the table

`table-bordered` adds borders to the table

`table-hover` enables a hover state

`table-condensed` makes the tables more compact by cutting cell padding in half

`table-responsive` makes a table responsive

## Images
`ing-responsive` makes an image responsive.

# Visibility
The `hidden` and `visible` classes can be used to make certain elements hidden or visible for specified for screen sizes
```
hidden-[size]
visible-[size]
```
