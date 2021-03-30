# Responsive Design

## Units
*Absolute* units are brittle and not generally responsive.

*Relative* units are more flexible!
* **em**: relative to the PARENT'S font size. This means that nested `em` styling will multiply each other!
* **rem**: relative to the ROOT ELEMENT's font size, so nested `rem` won't multiply each other!
* **vw**: 1% of viewport width 
* **vh**: 1% of viewport height
* **%**: Percentage of parent's size (i.e. parent's width, parent's height, etc) 

## Media Queries
A CSS **media query** lets you use different CSS style rules according to different screen sizes! For instance:

* `@media only screen and (max-width`... You know what? Just look up the syntax. Listing them out here is gonna be nuts, just remember that media queries are the way to declare different CSS behavior for different sizes of screen.

## Responsive Images
Images should change sizes according to screen resolution! This includes `img` tags AND `background-image` tags!

You can use a `<picture>` tag that contains `source srcset='[path]' media='max-width: {width}'` tags to load a different size of image for different situations.

The problem with this is that it takes a whole lot of tags in your HTML to do this. Ew!

## Responsive Font
`Type Scale` is a method of providing good, responsive fonts that function at multiple sizes

## The Grid System
Bootstrap (and many other CSS frameworks) offer a responsive grid system. And if you only want the grid system and nothing else, you can import just that system from the framework!

## SASS
SASS lets you create multiple CSS files (for organization) while still resulting in a single stylesheet for a browser to load (for performance)

It uses `.scss` files and compiles them into a single `.css` file.

### Nesting
SASS lets you nest selectors. For example:

```CSS
nav {
  .logo {
    /* Applies to .logo class elements within nav */
    :hover {
      /* Applies when you hover over .logo class elements within nav */
    }
  }

  ul {
    /* Applies to ul elements within nav!*/
  }
}
```

### Variables
SASS also supports variables!

```CSS
$base-font: Arial, Helvetica, sans serif;
$navColor: #ffccaa;

header {
  font: $base-font;
  color: $navColor;
}
```