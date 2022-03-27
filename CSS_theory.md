## Display

`:block` - this value allows you to set the height, width and margins. Each element starts with a new line and has 100% width.

`:inline` - this property allows elements to be displayed in a line as text. The height and width depend on the font parameters. 

`:inline-block` - this property allows elements to be displayed as blocks [they have height, width and margins], but they do not stretch the width by 100% and go one after the other. Can specify `width` and `height`. 

`:none` - Does not display an element and all child element are also no longer displayed. The document is rendered as if the element did not exist in the document tree  

`:table` - the element behaves like a table. For children: rows - `table-row`, cells - `table-cell`. 

`:flex` - flexbox container

`:list-item` - Behaves like a `<li>` element which allows it to define `list-style-type` and `list-style-position`. 

## Position

`:static` - default value. Properties doesnt work: `top`, `right`, `bottom`, `left`, `z-index`. 

`:relative` - the element remains in the normal flow of the document, but it can be shifted relative to its position in the document using the `top, bottom, right, left` properties. `z-index` is available. This means we can place elements on top of each other. 

`:absolute` - the element is removed from the normal document flow and becomes higher than all other elements of the normal flow. The element is positioned relative to the nearest parent with any positioning **other than static**. If there is no such thing, then it is positioned relative to the document. `top, right, bottom, left, z-index` are available. 

`:fixed` -  the element is removed from the normal document flow and becomes higher than all other elements of the normal flow. The element will always be in the browser's viewing area and positioned relative to the viewing area. `top, right, bottom, left, z-index` are available. 

`:sticky` - Sticky element -  the element remains in the normal flow of the document, then the element sticks to the nearest scrolling parent and scrolls with it.

## Selectors & Specificity

**Selectors main types:**

- `*` - any elements
- `div` - tag
- `#id`
- `.class`
- `[name="value"]` - attribute selectors 
- `:visited` - pseudo-classes

**Combinators**

A combinator is something that explains the relationship between the selectors.

- `div p` - descendant selector [all `p` elements inside `div`]. 
- `div > p` - child selector [first level]. 
- `div + p` - adjacent sibling selector [to select an element that is directly after another specific element]. 
- `div ~ p` - general sibling selector [selects all elements that are next siblings of a specified element]. 

**Specificity**

The browser determines what styles to show on an element depending on the specificity of CSS rules.

The specificity, four comma-separate values, `a, b, c, d` are calculated for each rule based on the following:

- `a` is whether **inline styles** are being used. If the property declaration is an inline style on the element, a is 1, else 0.
- `b` is the number of **ID selectors**.
- `c` is the number of **classes, attributes and pseudo-classes selectors**.
- `d` is the number of **tags and pseudo-elements selectors**.

**The resulting specificity is a matrix of values** that can be compared column by column. When comparing selectors to determine which has the highest specificity, look from left to right, and compare the highest value in each column. So a value in column `b` will override values in columns `c` and `d`, no matter what they might be.

**In the cases of equal specificity: the latest rule is the one that counts.** If you have written the same rule into your stylesheet (regardless of internal or external) twice, then the lower rule in your style sheet is closer to the element to be styled, it is deemed to be more specific and therefore will be applied.

The `!important` rule in CSS is used to add **more importance to a property/value** than normal.

In fact, if you use the `!important rule`, **it will override ALL previous styling rules for that specific property on that element!**

## Units

CSS has several different units for expressing a length.

**Absolute Lengths**

The absolute length units are fixed and a length expressed in any of these will appear as exactly that size.

Absolute length units are not recommended for use on screen, because screen sizes vary so much. However, they can be used if the output medium is known, such as for print layout. `cm, mm, inches (1in = 96px = 2.54cm), pixels (1px = 1/96th of 1in), points (1pt = 1/72 of 1in), picas (1pc = 12 pt)`

Pixels (px) are relative to the viewing device. For low-dpi devices, 1px is one device pixel (dot) of the display. For printers and high resolution screens 1px implies multiple device pixels.

**Relative Lengths**

Relative length units specify a length relative to another length property. Relative length units scale better between different rendering medium.

- **`em` - Relative to the font-size of the element (2em means 2 times the size of the current font).**
- `ex` - Relative to the x-height of the current font (rarely used). 
- `ch` - Relative to the width of the "0" (zero). 
- **`rem` - Relative to font-size of the root element.**
- `vw` - Relative to 1% of the width of the viewport*
- `vh` - Relative to 1% of the height of the viewport*
- `vmin` - Relative to 1% of viewport's* smaller dimension. 
- `vmax` - Relative to 1% of viewport's* larger dimension. 
- **`%` - Relative to the parent element.**

The em and rem units are practical in creating perfectly scalable layout!
*Viewport = the browser window size. If the viewport is 50cm wide, 1vw = 0.5cm.

## Resetting & Normalizing

**Resetting** - Resetting is meant to strip all default browser styling on elements. For e.g. `margin`s, `padding`s, `font-size`s of all elements are reset to be the same. You will have to redeclare styling for common typographic elements.

**Normalizing** - Normalizing preserves useful default styles rather than "unstyling" everything. It also corrects bugs for common browser dependencies.

I would choose resetting when I have a very customized or unconventional site design such that I need to do a lot of my own styling and do not need any default styling to be preserved.

## float

The `float` property is used for positioning and formatting content. For exapmle, let an image float left to the text in a container.

Floated elements remain a part of the flow of the page, and will affect the positioning of other elements (e.g. text will flow around floated elements).  [unlike `position: absolute` elements, which are removed from the flow of the page.]

The CSS `clear` property can be used to be positioned below `left/right/both` floated elements.

The float property can have one of the following values:

- `left` - The element floats to the left of its container
- `right` - The element floats to the right of its container
- `none` - The element does not float (will be displayed just where it occurs in the text). This is default
- `inherit` - The element inherits the float value of its parent

## overflow

The CSS `overflow` property controls what happens to content that is too big to fit into an area.

The overflow property specifies whether to **clip the content or to add scrollbars** when the content of an element is too big to fit in the specified area.

The overflow property has the following values:

- `visible` - Default. The overflow is not clipped. The content renders outside the element's box
- `hidden` - The overflow is clipped, and the rest of the content will be invisible
- `scroll` - The overflow is clipped, and a scrollbar is added to see the rest of the content
- `auto` - Similar to scroll, but it adds scrollbars only when necessary

The overflow property only works for block elements with a specified height.

## z-index

The `z-index` property in CSS controls the vertical stacking order of elements that overlap. `z-index` only affects elements that have a `position` value which is not `static`.

**Elements with non-static positioning** (and their children) will always appear on top of elements with default static positioning, regardless of HTML hierarchy.

A stacking context is an element that contains a set of layers.

An element can have a positive or negative stack order. 

## Flex & Grid

**Flexbox** is mainly meant for 1-dimensional layouts while **Grid** is meant for 2-dimensional layouts.

**Flexbox solves many common problems in CSS**, such as vertical centering of elements within a container, sticky footer, etc. Bootstrap is based on Flexbox, and it is probably the recommended way to create layouts these days. Have tried Flexbox before and I use it all the time. 

Grid is by far the most intuitive approach for creating grid-based layouts (it better be!) but browser support is not wide at the moment.

Flexbox layout is most appropriate to the components of an application, and small-scale layouts, while the Grid layout is intended for larger scale layouts.

### Flex 

- aims at providing a more efficient way to lay out, align and distribute space among items in a container. 

The main idea behind the flex layout is to give the container the ability to change its items width/height to best fill the available space. **A flex container expands items to fill available free space or shrinks them to prevent overflow.**

<img width="561" alt="Снимок экрана 2022-03-24 в 15 49 30" src="https://user-images.githubusercontent.com/57959373/159910270-7845c6ec-3144-4d62-a1bd-d55a056f3566.png">

Items will be laid out following either the main axis (from main-start to main-end) or the cross axis (from cross-start to cross-end).

`main axis` – The main axis of a flex container is the primary axis along which flex items are laid out. Beware, it is **not necessarily horizontal**; it depends on the **flex-direction property**.

`cross axis` – The axis **perpendicular to the main axis** is called the cross axis. Its direction depends on the main axis direction.

`main-start | main-end` – The flex items are placed within the container starting from main-start and going to main-end.

**Flexbox properties [flex container]**

`dispay: flex | inline-flex` - It enables a flex context for all its direct children. `flex` value - the flex-container stay at full width. `inline-flex` - flex-container does not take up the entire widt, and acts as `inline-block` prop. 

`flex-direction: row | row-reverse | column | column-reverse` - This establishes **the main-axis**, thus defining the direction flex items are placed in the flex container. 

**`justify-content: flex-start | flex-end | center | space-between | space-around | space-evenly | start | end | left | right ... + safe | unsafe`** - This defines **the alignment along the main axis.** It helps distribute extra free space leftover. 

- `flex-start` (default): items are packed toward the start of the flex-direction.
- `flex-end`: items are packed toward the end of the flex-direction.
- `center`: items are centered along the line
- `space-between`: items are evenly distributed in the line; **first item is on the start line, last item on the end line**. 
- `space-around`: items are evenly distributed in the line **with equal space around them**. Visually the spaces aren’t equal, since all the items have equal space on both sides. 
- `space-evenly`: items are distributed so that **the spacing between any two items is equal**.

Note that that browser support for these values is nuanced. For example, `space-between` never got support from some versions of Edge, and `start/end/left/right` aren’t in Chrome yet. The safest values are `flex-start, flex-end, and center`.

**`align-items: stretch | flex-start | flex-end | center | baseline | first baseline | last baseline | start | end | self-start | self-end + ... safe | unsafe`** - This defines the default behavior for **how flex items are laid out along the cross axis on the current line.** 

- `stretch` (default): stretch to fill the container (still respect min-width/max-width)
- `flex-start`: items are placed **at the start of the cross axis**.
- `flex-end`: items are placed **at the end of the cross axis**. 
- `center`: items are **centered in the cross-axis**. 
- `baseline`: items are aligned such as their baselines align. 

`flex-wrap` - By default, flex items will all try to fit onto one line. You can change that and allow the items to wrap as needed. `.container { flex-wrap: nowrap | wrap | wrap-reverse; }`

`flex-flow` - This is a shorthand for the flex-direction and flex-wrap properties, which together define the flex container’s main and cross axes. The default value is row nowrap. `flex-flow: row wrap;`

**Flexbox properties [flex items]**

`order` - By default, flex items are laid out in the source order. However, the order property controls the order in which they appear in the flex container. `.item { order: 5; }`

`flex-grow` - This defines the **ability for a flex item to grow if necessary**. It accepts a unitless value that serves as a proportion. It dictates what amount of the available space inside the flex container the item should take up. `.item { flex-grow: 4; }`

> If all items have `flex-grow` set to `1`, the remaining space in the container will be distributed **equally to all children**. If one of the children has a value of `2`, that child would take up **twice as much of the space either one of the others**.

`flex-shrink` - This defines the ability for a flex item to shrink if necessary. `.item { flex-shrink: 3; }`

`flex-basis` - This defines the default size of an element **before the remaining space is distributed**. It can be a length (e.g. 20%, 5rem, etc.) or a keyword. The `auto` keyword means “look at my width or height property”. `.item { flex-basis:  | auto; }`

> If set to 0, the extra space around content isn’t factored in. If set to auto, the extra space is distributed based on its flex-grow value.

`flex` - This is the shorthand for `flex-grow`, `flex-shrink` and `flex-basis` combined. The second and third parameters (flex-shrink and flex-basis) are optional. The default is `0 1 auto`, but if you set it with a single number value, like `flex: 5;`, that changes the flex-basis to 0%, so it’s like setting `flex-grow: 5; flex-shrink: 1; flex-basis: 0%;`.

`.item { flex: none | [ <'flex-grow'> <'flex-shrink'>? || <'flex-basis'> ] }`

`align-self` - This allows the default alignment (or the one specified by `align-items`) to be overridden for individual flex items.

`.item { align-self: auto | flex-start | flex-end | center | baseline | stretch; }`

### Grid

- is a two-dimensional grid-based layout system. 

To get started you have to define a container element as a grid with `display: grid`, set the column and row sizes with `grid-template-columns` and `grid-template-rows`, and then place its child elements into the grid with `grid-column` and `grid-row`.

**Properties for the Parent [Grid Container)]**

`display: grid | inline-grid;` - Defines the element as a grid container. `grid` – generates a block-level grid. `inline-grid` – generates an inline-level grid. 

`grid-template-columns & grid-template-rows` - Defines the columns and rows of the grid with a space-separated list of values. The values represent the **track size, and the space between them** represents the grid line.

```css
 grid-template-rows: 1fr 1fr 1fr;
 grid-template-columns: repeat(3 , 1fr)
```

The shorthand: `grid-template: none | <grid-template-rows> / <grid-template-columns>;`

```css
.container {
  grid-template: 1fr 1fr / 1fr 1fr;
}
```

**The unit of length `fr` is a fraction of the available space in the grid container**. The `fr` unit (a “fraction”) can be used when defining grids like any other CSS length such as ``%, px, em``. It allows you to create elastic (flexible) grid tracks. 

**Grid lines are automatically assigned positive numbers** from these assignments (-1 being an alternate for the very last row).

We also can choose to explicitly name the lines. Note the bracket syntax for the line names:

```css
.container {
  grid-template-columns: [first] 40px [line2] 50px [line3] auto [col4-start] 50px [five] 40px [end];
  grid-template-rows: [row1-start] 25% [row1-end] 100px [third-line] auto [last-line];
}
```

`grid-template-areas` - Defines a grid template by referencing the names of the grid areas which are specified with the grid-area property.

For example, we want to create an application with a header, sidebar, main area and footer. We will set the `grid-area` property to each of these elements.  And set the `grid-template-areas` property to the container, we will be able to arrange these elements in a container.

```css
.item-a {
  grid-area: header;
}
.item-b {
  grid-area: main;
}
.item-c {
  grid-area: sidebar;
}
.item-d {
  grid-area: footer;
}

.container {
  display: grid;
  grid-template-columns: 50px 50px 50px 50px;
  grid-template-rows: auto;
  grid-template-areas: 
    "header header header header"
    "main main . sidebar"
    "footer footer footer footer";
}
```
That’ll create a grid that’s four columns wide by three rows tall. The entire top row will be composed of the header area. The middle row will be composed of two main areas, one empty cell, and one sidebar area. The last row is all footer.

Repeating the name of a grid area causes the content to span those cells.

In order for the **header** to be the full length of the screen, we must repeat it as many times as we have columns in the application.

<img width="368" alt="Снимок экрана 2022-03-27 в 20 08 27" src="https://user-images.githubusercontent.com/57959373/160290372-38ffef2c-c23d-461c-a642-0d06258d07d3.png">

**grid gap** - Specifies the size of the grid lines. Set the width of the gutters between the columns/rows.

```css
.container {
  column-gap: <line-size>;
  row-gap: <line-size>;
}
```

or: 

```css
gap: <grid-row-gap> <grid-column-gap>;
```










