# CSS Style Guide

A collection of CSS lessons learned the hard way.

## Basics

### Tabs or Spaces?

Use **spaces only**, with **2 spaces** per indentation level. Never mix tabs and spaces.

### Blank Lines

Separate selector blocks with a single blank line.

### Trailing Whitespace

Do not include trailing whitespace on any lines.

## Selectors

Prefer descriptive class names over descendent selectors. Namespace selectors to improve clarity and reduce conflicts.

```sass
// Good
.task-item-label {
  #...
}
// Bad
li.task-item label {
  #...
}
```

Mark Otto wrote a more detailed explanation [on his blog](http://markdotto.com/2012/03/02/stop-the-cascade/).

## Nesting

As a general rule, don't nest more that two levels and try to keep nested blocks short. Up to 3 levels may be acceptable in some cases, but you should never nest further than that. If you can, avoid nesting by separating rules into small logical groups instead of long groups of semi-related styles.

Nesting is very helpful to define element states such as active and hover, pseudo elements like before and after, and minimal child selectors that don't justify an additional class name.

```
TODO
```

## Line Length

Avoiding excessive nesting (see above) should ensure that your line length is never much more than 80 chars. An exception to this is background gradient declarations which can easily extend far beyond that.  At this time we don't have a work-around as SASS does not allow rules to span multiple lines.  For common gradient types (eg. stops at 0%, 50%, 50%, 100%) we can create a sass mixin to slightly reduce the line length (although even just 4 RGBA declarations alone can total 80+ chars)

## Organization

Thanks to compilation and compression, we're able to organize styles into many small files without impacting the end user. Rules should be organized into small sets corresponding to the elements they style. Styles of unrelated elements should never be in the same file.

Complicated elements, such as a sidebar, might require hundreds of lines to style. In these cases, it's often appropriate to separate the related styles into multiple files in a subdirectory, such as `sidebar/`.

### Style Block Orgainization

In order to keep application styles easy for anyone to jump into and work with it's imporatant to keep style block organization consistent.

There are no hard-and-fast rules here, but some tips are:

- Include mixins at the top of style blocks instead of scattered throughout each style block to make a selector's inherited properties obvious
- Pick an order for style properties and stick to it (alphabetical, by category, etc)
- Place parent element styles (if any) at the top of a style block, followed by pseudo selectors and finally nested child selectors (with a space seperating them from parent styles)

## Maintainability

Consider an example:

```sass
.segmented .focus-bar-button
  &.selected:before,
  &:active:before,
  &.selected + li:before,
  &:active + li:before,
  &:first-child:before
    display: none
```

## Property ordering

Group by "Positioning", "Display & Box Model", "Font", "Aesethtics", "Flexbox", etc

https://github.com/necolas/idiomatic-css

This rule obviously hides something, but it's not clear what it's hiding, or why. This code is unmaintainable, because its purpose is not obvious. Strive to write selectors and styles whose purpose and relationship is intuitive and obvious.

## Other Resources
- http://markdotto.com/2012/03/02/stop-the-cascade/
- http://markdotto.com/2012/02/16/scope-css-classes-with-prefixes/
- http://www.adobe.com/devnet/html5/articles/css-everything-is-global-and-how-to-deal-with-it.html

## TODO

* Comment format
* Before/After examples
* Examples of good styles
