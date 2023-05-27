# Table of Contents
- [Table of Contents](#table-of-contents)
- [References](#references)
- [Introduction](#introduction)
- [Responsive Content](#responsive-content)
  - [Content Strategy](#content-strategy)
- [HTML for Responsiveness](#html-for-responsiveness)
- [Media Queries](#media-queries)
  - [Other Ways to Use Media Queries](#other-ways-to-use-media-queries)
  - [What Can Be Queried](#what-can-be-queried)
  - [Breakpoints and Design Ranges](#breakpoints-and-design-ranges)
- [Progressive Enhancement](#progressive-enhancement)
- [Responsive Images](#responsive-images)

# References
> **Learning Responsive Web Design** by *Clarissa Peterson*
> 
> **Implementing Responsive Design** by *Tim Kadlec*

# Introduction
Responsive web design is a way to make websites that can be easily viewed and used on any type of device and size of screen.

# What to Consider
1. Type of device: smartphone, laptop, tablet. TV, refrigerator, ebook reader, tts
2. Display size
3. Network speed
4. Standards support
5. Input method
6. Context: How and where the device is used - the time of day, around friends or strangers, at home, while walking, in transit
7. Js or CSS functionality
8. Accessibility for disabled  people - color blindness, blindness, 

# Responsive Layout
## Layout Options
1. Fixed-width Layout
    Site width is constrained to a specific pixel measurement, usually 960px.
2. Fluid Layout
    Dimensions are determined by percentages.
## Flexible Grids

# Responsive Content
## Content Strategy
When redesigning, do a content audit - going through the site examining the content before designing.

Use the inverted pyramid, putting the most important information first.

Make use of headings for particularly long content to split them into sections.

## Responsive Typography

## Responsive Images
```css
img {max-width: 100%;}
```

Using the `srcset` attribute with the `<img>` tag to swap out images. The browser only downloads the file it needs.
```html
<img src="images/flower.jpg" alt="A flower" srcset="images/flower-HD.jpg 2x, images/flower-small.jpg 600w, images/flower-small-HD,jpg 600w 2x">
```
* Default image: `flower.jpg`
* For high-density screens(pixel density of 2 or greater): `flower-HD.jpg`
* Narrow screens < 600px wide: `flower-small.jpg`
* Screens < 600px and high density: `flower-small-HD.jpg`


Using the `srcset` attribute with the `<picture>` tag to swap out images. The browser only downloads the file it needs.
```html
<picture>
  <source media="(min-width:45em)" src="images/flower-large.jpg"> //45ems or wider
  <source media="(min-width: 18em)" src="images/flower-medium.jpg"> //18ems or wider, but less than 45ems   
  <source src="flower-small.jpg"> //All other viewports
  <img src="images/flower-small.jpg" alt="A flower">
</picture>
```

You can combine the `<picture>` element with the `srcset` attribute if you want to use both viewport media queries and versions with different resolutions
```html
<picture>
  <source media="(min-width:45em)" srcset="flower-large.jpg 1x, flower-large-hd.jpg 2x"> //45ems or wider
  <source media="(min-width: 18em)" srcset="flower-medium.jpg 1x, flower-medium.jpg 2x">  //18ems or wider, but less than 45ems
  <source srcset="flower-small.jpg 1x. flower-small-hd.jpg 2x"> //All other viewports
  <img src="flower-small.jpg" alt="A flower">
</picture>
```

Another solution would be to use
1. Polyfills such as Picturefill, Adaptive Images, HiSRC, 
2. Third-party services such as ReSRC, Thumbr.io, Responsive.io

# HTML for Responsiveness

1. Write clean and semantic HTML
2. Separate content from presentation


# Media Queries
`@media only screen`  
The `only` keyword is used for browsers that only support CSS2 media queries. Initially, they would override existing styles on every screen with the styles in the media queries. By adding `only`, they don't apply them at all.

`@media only screen and`  
Media queries can only use `or` or `not`.

`@media only screen and (min-width: 40em)`
Each expression goes inside parentheses unless it's a one-word expression e.g media type 

When creating media queries, start from the smallest viewport and work upward.

## Other Ways to Use Media Queries
1. Linking Stylesheets for Media Queries
```html
<link rel="stylesheet" href="styles.css">
<link rel="stylesheet" href="print.css" media="print"> //For just print
```
You could also import the stylesheet.

2. Using Media Queries with Attributes
A media query can be used as an attribute to the `<style>` element in the `<head>` of a page
```html
<style media="only screen and (min-width: 40em)">
...
</style>
```

## What Can Be Queried
1. viewport/device width and height
```css
//For viewport
@media only screen and (min-width: 40em){...}
@media only screen and (height: 60em){...}

//For device
@media only screen and (max-device-width: 40em){...}
```

2. Orientation
`Landscape` or `portrait`
```css
@media only screen and (orientation: landscape){...}
```

3. Aspect ratio
`aspect-ratio`: ratio of viewport
`device-aspect-ratio`: ratio of device screen
```css
@media only screen and (device-aspect-ratio: 16/9){...}
@media only screen and (min-device-aspect-ratio: 1920/1080){...}
```

4. Resolution
```css
@media only screen and (min-resolution: 300dpi){...}
```
5. `color`: number of bits per color component of the output device. The word `color` on its own asks if the device has a color screen or not.
6. `color-index`: number of entries in the color lookup table of the device e.g 256
7. `monochrome`
8. `scan`: whether device uses progressive scan. Only applies to Tvs.
9. `grid`: Checks if the output is grid-based (such as teletype or TTY, with a fixed font) or bitmap(a screen with pixels).

## Breakpoints and Design Ranges
A breakpoint is the point at which you can use a media query to change the design.

Design range is the range of screen sizes on either side of the line. Each design range gets a different variation of the design.

The important thing is how a design look across each design range, not how it looks at each breakpoint.

# Progressive Enhancement
Starting with the basics, and adding on from there for browsers and devices that can handle more.  
Building for the less-capable browsers first. 

1. Default Layer: Build for the narrowest devices and the most basic devices - devices that may not be able to recognize media queries, CSS3 or JS. Use semantic markup and structure, and focus on presenting the content in a clean, usable form.
2. Presentation Layer: Use CSS to determine how everything will look on the page - layout, color, typography, etc.
3. Behaviour layer: Try to make sure basic site functionality will work without JS. Add JS.




# Responsive Workflow
## Content
The content is the most important part of the website. Build the design around the content.

Use a style guide; a document to collate all the design decisions made for the site.
It also documents design decisions for the future maintainer of the site, and helps maintain a website's design identity over time.
1. What colors are used?
2. What typefaces are used, and where?
3. The correct font sizes
4. What the buttons look like?
5. Layout system/grid
6. Styles for elements e.g list items, form elements, blockquotes, etc
7. Logo usage

A good example to start is the [Style Guide Boilerplate](http://brettjankord.com/projects/style-guide-boilerplate/)
