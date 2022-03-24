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





