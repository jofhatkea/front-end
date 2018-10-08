# Position

## CSS position, 5 values

1. `static`
2. `relative`
3. `absolute`
4. `fixed`
5. `sticky`

## 5 "helpers"

1. `top`
2. `left`
3. `bottom`
4. `right`
5. `z-index`

The 5 helper-propteries does NOT work on non-positioned elements, including `static`

### `static`

Default value

The element is positioned in the normal order

Use it to reset position.

### `relative`

Move an element, relative to it's original position.

This leaves an empty space where it used to be, and elements can now overlap.
`position: relative` does NOT affect other elements position!

### `absolute`

Move an element relative to it's first positioned parent (not `static`), if it has no positioned parent, `<html>` is used

The space left behind is filled up by other elements. In practice, think of the element being removed from the HTML and placed on top.

### `fixed`

Position an element relative to the viewport

The element is not affected by scrolling

### `sticky`

[Does not work in all browsers](https://caniuse.com/#feat=css-sticky)

A mix between `relative` and `fixed`. Behaves normally until it's condition is met, then it becomes `fixed`.

It stays fixed until another element "pushes it"
