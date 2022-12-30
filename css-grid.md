# References
> **Designing with CSS Grid Layout** by *Ahmad Ajmi, Nitish Kumar and Adrian Roworth*
> 
> **Get Ready for CSS Grid Layout** by *Rachel Andrew*


# Introduction
A layout system that allows us to design pages using a 2-d grid.

# Creating a Grid
![Grid Example](img/grid-creating-grids.png)

```html
<div class="app-layout">
  <div class="tweets">Tweets</div>
  <div class="replies">Replies</div>
  <div class="search">Search</div>
  <div class="messages">Messages</div>
</div>
```

```css
.app-layout {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr 1fr; /*The container is divided into four equal columns*/
  grid-template-rows: 100vh;
}
```

Applying `display:grid;` to the element makes it a grid container.

The `grid-template-columns` property specifies the width of each grid column in the grid.

The `grid-template-rows` specifies the height of each grid row.

