# CSS

## Agenda
* New project: Tweeter
* BOX model
* Web layout: floats
* Web layout: FLEXBOX TO THE RESCURE


## Single-Page Apps
A **`Single-Page App`** (SPA) is an application that consists of only one page, which dynamically changes as it sends and receives data to/from the server.

Think Twitter, where you scroll and scroll and scroll and scroll and the page continues forever!

**TinyApp** was a multi-page site - we routed the user to different pages when they clicked around.

We will be using **`Ajax`** to send data with HTML forms.

## CSS
CSS (Cascading StyleSheets) can be FIDDLY. You know this. You remember the bar chart project? Yeah. You remember the bar chart project.

### BOX Model
ALmost every HTML element can be represented with a box!

CONTENT lives in the middle of the box.
PADDING is the spacing between the CONTENT and the BORDER.
BORDER is the line (visible or invisible) that exists around the PADDING.
MARGIN is the spacing around a BORDER that separates an element from the MARGIN of other elements.

### The Role of CSS
CSS is almost solely responsible for anytihng on the internet looking good. Any styling you want to add to a website that's built on HTML, you need to add with CSS. You might be using JavaScript to modify the CSS, but it's still CSS at the end of the day!

### Example

```CSS
.box {
  width: 200px;
  height: 200px;
  border: 3px dashed darkgrey;
  /* Look! Some CSS styles support multiple values.  We can use the above instead of:
  border-width: 3px;
  border-style: dashed;
  border-color: darkgrey;
  */

  padding: 10px 5px 2px 3px;
  /* Similarly, this is a shortcut for:
  padding-top: 10px
  padding-right: 5px
  padding-bottom: 2px
  padding-left: 3px
  */

  margin: 1em;
  /* 'em' is a relative size! It's relative to:
      - the font size of the element's parent if used for typography (i.e. setting 'font-size')
      - the font size of the element itself if used for other properties (such as 'width') */
}
```

### The `box-sizing` Property
CSS, by default, sets `width` values to be the INTERNAL size of the box - i.e. the CONTENT section will be set to `width`.

The `box-sizing` property of the `body` element can change this!
* `box-sizing: content-box` uses CONTENT for `width`
* `box-sizing: border-box` uses CONTENT+PADDING+BORDER for width. Holy crap! That's extremely useful!

**JUST BE CONSISTENT, THOUGH.**

## Web Layout - Floats
**Floats** may show up in legacy CSS code.

Before Flexbox, we used floats for web layout. Float elements aren't part of the normal flow of the document, and can be "floated" to the left or right of the page.

**Floats** are aggravating. You remember this. Yeesh.

## Web Layout: Flexbox
Look at me. LOOK AT ME. **`Flexbox`** is the captain now.

The **flexible box** gives a better way to lay out, align, and distribute space among items (flex items) in a container, even when their size is dynamic or unknown! Woo!

### Flex-Grow
`flex-grow` allows content to dynamically expand to occupy space. The default is `1`, meaning that it takes up **1x** its allotment in the container.

`flex-grow: 2;` will make that element take up more space compared to default ones.

`flex-grow` makes elements take up all available space in the container!