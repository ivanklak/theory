## Display

`:block` - this value allows you to set the height, width and margins. Each element starts with a new line and has 100% width.

`:inline` - this property allows elements to be displayed in a line as text. The height and width depend on the font parameters. 

`:inline-block` - this property allows elements to be displayed as blocks [they have height, width and margins], but they do not stretch the width by 100%, but go one after the other.

`:none` - the elements are not displayed. 

`:table` - the element behaves like a table. For children: rows - `table-row`, cells - `table-cell`. 

`:flex` - flexbox container

## Position

`:static` - default value. Properties doesnt work: `top`, `right`, `bottom`, `left`, `z-index`. 

`:relative` - the element remains in the normal flow of the document, but it can be shifted relative to its position in the document using the `top, bottom, right, left` properties. `z-index` is available. This means we can place elements on top of each other. 

`:absolute` - the element is removed from the normal document flow and becomes higher than all other elements of the normal flow. The element is positioned relative to the nearest parent with any positioning **other than static**. If there is no such thing, then it is positioned relative to the document. `top, right, bottom, left, z-index` are available. 

`:fixed` -  the element is removed from the normal document flow and becomes higher than all other elements of the normal flow. The element will always be in the browser's viewing area and positioned relative to the viewing area. `top, right, bottom, left, z-index` are available. 

`:sticky` - Sticky element -  the element remains in the normal flow of the document, then the element sticks to the nearest scrolling parent and scrolls with it.

## Selectors & Specificity

Main types: 

- `*` - any elements
- `div` - tag
- `#id`
- `.class`
- [name="value"] - selector on attribute 
- `:visited` - pseudo-classes

The browser determines what styles to show on an element depending on the specificity of CSS rules.

The specificity, four comma-separate values, `a, b, c, d` are calculated for each rule based on the following:

- `a` is whether **inline styles** are being used. If the property declaration is an inline style on the element, a is 1, else 0.
- `b` is the number of **ID selectors**.
- `c` is the number of **classes, attributes and pseudo-classes selectors**.
- `d` is the number of **tags and pseudo-elements selectors**.

**The resulting specificity is a matrix of values** that can be compared column by column. When comparing selectors to determine which has the highest specificity, look from left to right, and compare the highest value in each column. So a value in column `b` will override values in columns `c` and `d`, no matter what they might be.

**In the cases of equal specificity: the latest rule is the one that counts.** If you have written the same rule into your stylesheet (regardless of internal or external) twice, then the lower rule in your style sheet is closer to the element to be styled, it is deemed to be more specific and therefore will be applied.

