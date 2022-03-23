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

