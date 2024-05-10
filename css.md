---
title: CSS
---
# CSS

- [Introduction](#introduction)
- [SASS](#sass)
- [LESS](#less)
- [CSS](#css)

<a name="introduction"></a>
## Introduction
There are many projects out there using different preprocessors and some which don't use any preprocessors. Here we shall link to our own rules and the style guides that belong to SASS / LESS and any preprocessor that is used in the future.

<a name="avoid-using-ids-for-styling"></a>
## Avoid using IDs for any styling
An ID should only be used once per page. So using them for styling is not suitable, as the CSS is less likely to be reusable.

<a name="sass"></a>
## SASS 
SASS style guide is covered [here](https://github.com/bigcommerce/sass-style-guide).

<a name="less"></a>
## LESS
There are not currently any standards set in stone by Netmatters.

<a name="css"></a>
## CSS 
### Plan your CSS
Before diving in and writing huge chunks of CSS, plan your styles carefully. What general styles are going to be needed, what different layouts do you need to create, what specific overrides need to be created, and are they reusable? Above all, you need to try to avoid too much overriding. If you keep finding yourself writing styles and then cancelling them again a few rules down, you probably need to rethink your strategy.

### Use flexible/relative units
For maximum flexibility over the widest possible range of devices, it is a good idea to size containers, padding, etc. using relative units like ems and rems or percentages and viewport units if you want them to vary depending on viewport width. You can read some more about this in our guide to CSS values and units.

### Don't use resets
For maximum control over CSS across platforms, a lot of people used to use CSS resets to remove every style, before then building things back up themselves. This certainly has its merits, but especially in the modern world, CSS resets can be an overkill, resulting in a lot of extra time spent reimplementing things that weren't completely broken in the first place, like default margins, list styles, etc.

If you really feel like you need to use a reset, consider using normalize.css by Nicolas Gallagher, which aims to just make things more consistent across browsers, get rid of some default annoyances that we always remove (the margins on <body>, for example) and fix a few bugs.

### !important
!important is the last resort that is generally used only when you need to override something and there is no other way to do it. Using !important is a bad practice and you should avoid it wherever possible.

```
.bad-code {
  font-size: 4rem !important;
}
```

### CSS comments
Use CSS-style comments to comment code that isn't self-documenting. Also note that you should leave a space between the asterisks and the comment.

```
/* This is a CSS-style comment */
```

Put your comments on separate lines preceding the code they are referring to, like so:

### Double quotes around values
Where quotes can or should be included, use them, and use double quotes. For example:

```
[data-vegetable="liquid"] {
  background-color: goldenrod;
  background-image: url("../../media/examples/lizard.png");
}
```

### Longhand vs. shorthand rules
Usually, when teaching the specifics of CSS syntax, it is clearer and more obvious to use longhand properties, rather than terse shorthand (unless, of course, you're explaining shorthand through the example). Remember that the point of examples on MDN Web Docs is to teach people, not to be clever or efficient. We explain here why writing with longhand rules is recommended.

It is often harder to understand what the shorthand is doing. In the example below, it takes a while to pick apart exactly what the font syntax is doing.

```
font: small-caps bold 2rem/1.5 sans-serif;
```

Whereas the following style is clearer:

```
font-variant: small-caps;
font-weight: bold;
font-size: 2rem;
line-height: 1.5;
font-family: sans-serif;
```

CSS shorthand comes with potential added pitfalls — default values are set for parts of the syntax that you don't explicitly set, which can produce unexpected resets of values you've set earlier in the cascade or other expected effects. The grid property, for example, sets all of the following default values for items that are not specified:
* grid-template-rows: none
* grid-template-columns: none
* grid-template-areas: none
* grid-auto-rows: auto
* grid-auto-columns: auto
* grid-auto-flow: row
* column-gap: 0
* row-gap: 0
* column-gap: normal
* row-gap: normal

Some shorthands only work as expected if you include the different value components in a certain order. This is the case in CSS animations. In the example below, the expected order is written as a comment:
```
/* duration | timing-function | delay | iteration-count
  direction | fill-mode | play-state | name */
animation: 3s ease-in 1s 2 reverse both paused slidein;
```
In this example, the first value that can be parsed as a <time> is assigned to the animation-duration property, and the second value that can be parsed as time is assigned to animation-delay. (For more information, see animation syntax details.)

### Mobile-first media queries
In a stylesheet that contains media query styles for different target viewport sizes, first include the narrow screen/mobile styling before any other media queries are encountered. Add styling for wider viewport sizes via successive media queries. Following this rule has many advantages that are explained in the Mobile First article.

```
/* Default CSS layout for narrow screens */

@media (min-width: 480px) {
  /* CSS for medium width screens */
}

@media (min-width: 800px) {
  /* CSS for wide screens */
}

@media (min-width: 1100px) {
  /* CSS for really wide screens */
}
```

### Selectors
Don't use ID selectors because they are:
less flexible; you can't add more if you discover you need more than one.
harder to override because they have higher specificity than classes.

**Good**
```
.editorial-summary {
  /* ... */
}
```
**Bad**
```
#editorial-summary {
  /* ... */
}
```

### Value to turn off properties
When turning off borders (and any other properties that can take 0 or none as values), use 0 rather than none:

```
border: 0;
```

## Sources
https://developer.mozilla.org/en-US/docs/MDN/Writing_guidelines/Writing_style_guide/Code_style_guide/CSS
https://github.com/bigcommerce/sass-style-guide
