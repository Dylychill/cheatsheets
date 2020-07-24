# CSS

Note: Stylesheets load in order. The last sheet loaded, or the last selector in a sheet, will take priority.

### Selectors

**element**
```css
img {
    /* all these styles apply to every <img> */
}
```

**classes**
```css
.class-name {
    /* all these styles apply to everything with this class*/
}
```

**id**
``` css
#my-element {
    /* only items with this id */
}
```


```css
.my-wrapper .my-class{
    /* will apply only to "my-class" elements that are WITHIN "my-wrapper" */
}

.class-one, .class-two{
    /* applies to both classes */
}

.class-one > .child {
    /* only direct children */
}

.class-one.class-two {
    /* must have BOTH of these classes */
}
```

### Pseudoselectors

```css
.my-class:hover{}

.my-class:focus{}

.my-class:first-child{
    /* only the first child WITHIN my-class */
}

.my-class:nth-child(3){
    /* only the 3 child in my-class */
}
```

### Units
- `px`
- `%`: percentage of the elements parent
- `vw`/`vh`: percentage viewheight or viewwidth
- `rem`: ratio of the root font-size

### Some basic css rules

```css
.class{
    color: blue; /* for text color */
    background: red; /* background color */
    width: 10px;
    height: 10%;
    margin: 20px; /* outside the element */
    padding: 20px; /* inside */
    font-size: 10px;
    font-family: 'Avenir', Helvetica;
}
```

### Position
- `relative`: They will be arranged based on their siblings.
- `absolute`: removes the element from the "flow" of sibling elements. Instead, it becomes positioned based on its closest parents that has "relative" positioning. You can use `top`,`bottom`,`left`, and `right` to move it around precisely.
- Note: either "relative" or "absolute" positioning gives you the ability to use `z-index`
- Note: Until you put relative position on the parent, you cannot set a child as absolute. Needs a parent to be relative to.

### Display

- `block` (default)
- `inline-block` (stack horizontally)
- `none` does not get put into the DOM, hidden
- `flex` sets up for flex box stuff

### Flexbox

```css
.parent{
    display:flex;
    flex-direction:column; /* or row */
    align-items:center; /* or flex-start, flex-end, space-between, space-around, space-evenly */
    justify-content:center;
    flex-wrap:wrap; /* allows your children to wrap */
}

.child {
    flex:1; /* the ratio of how much space to take up */
    /* Grow along the axis of the parents flex direction as much as you can */
}
```
- `align-items` aligns opposite the direction axis
- `justify-content`: aligns items on the direction axis

\![Flexbox cross and main axis diagram](\flexbox.PNG)

### response CSS
```css
html { /* MOBILE */
  font-size: 15px;
}

@media (min-width: 400px) {
  html { /* TABLET */
    font-size: 18px;
  }
}

@media (min-width: 768px) {
  html { /* DESKTOP */
    font-size: 21px;
  }
}
```
- you can use `rem` units to scale other elements on your page in relation to that `font-size` on your `<html>` element.
- Note: font size is sort of special, cause you really need that to be legible and it can't get that small or large and be reasonable.