# notes-for-may4th

## Start big and work your way down
We already have our Page up there, now let’s map out the Organisms using a red marker. We‘re skipping the Template since it’s basically the skeleton of the page without the pictures and the actual data, however, it is still an important step when designing or building a product.
Since we are working our way down, We can’t define Organisms using molecules as Brad Frost did. So we’ll come up with our own definition.

### Organisms
* Large sections that can easily be extracted from the page.

### Molecules
* Sections you can easily extract from an **ORGANISM**.

### Atoms
* The smallest part of an element that can exist they include HTML elements like: 
- Labels
- Inputs
- Buttons

## Step Process
1. Split the page design into large sections — Organisms
2. Next, divide your Organisms into Molecules, Look out for sections that are repeated frequently
3. Then, Extract your atoms from the Molecules. Remember elements that can’t be broken up any further

## For components to be reusable and composable, you have to make them as small and as independent as possible.


# This whole fuckin page is useful
* https://medium.com/backticks-tildes/visually-breaking-down-ui-components-using-atomic-design-and-building-with-react-part-2-20eb8aabab4b

## Callbacks
*  A callback is a function that is to be executed after another function (normally asynchronous) has finished executing.
- In JavaScript, functions are objects. Because of this, functions can take functions as arguments, and can be returned by other functions. Functions that do this are called higher-order functions. Any function that is passed as an argument and subsequently called by the function that receives it, is called a callback function.
# Responsive Web Design
* Responsive web design is the practice of building a website suitable to work on every device and every screen size, no matter how large or small, mobile or desktop. Responsive web design is focused around providing an intuitive and gratifying experience for everyone. Desktop computer and cell phone users alike all benefit from responsive websites.
## Responsive vs. Adaptive vs. Mobile
* Responsive and adaptive web design are closely related, and often transposed as one in the same. Responsive generally means to react quickly and positively to any change, while adaptive means to be easily modified for a new purpose or situation, such as change. With responsive design websites continually and fluidly change based on different factors, such as viewport width, while adaptive websites are built to a group of preset factors. A combination of the two is ideal, providing the perfect formula for functional websites. Which term is used specifically doesn’t make a huge difference.
* **Mobile**, on the other hand, generally means to build a separate website commonly on a new domain solely for mobile users. While this does occasionally have its place, it normally isn’t a great idea. Mobile websites can be extremely light but they do come with the dependencies of a new code base and browser sniffing, all of which can become an obstacle for both developers and users.
# Flexible Layouts
* Responsive web design is broken down into three main components, including flexible layouts, media queries, and flexible media. The first part, flexible layouts, is the practice of building the layout of a website with a flexible grid, capable of dynamically resizing to any width. Flexible grids are built using relative length units, most commonly percentages or em units. These relative lengths are then used to declare common grid property values such as width, margin, or padding.
* Flexible layouts do not advocate the use of fixed measurement units, such as pixels or inches. Reason being, the viewport height and width continually change from device to device. Website layouts need to adapt to this change and fixed values have too many constraints. Fortunately, Ethan pointed out an easy formula to help identify the proportions of a flexible layout using relative values.
```
Target + Context = Result
```
# Flexible Grid
```html
<div class="container">
  <section>...</section>
  <aside>...</aside>
</div>
```
```css
.container {
  width: 538px;
}
section,
aside {
  margin: 10px;
}
section {
  float: left;
  width: 340px;
}
aside {
  float: right;
  width: 158px;
}
```
* Using the flexible grid formula we can take all of the fixed units of length and turn them into relative units. In this example we’ll use percentages but em units would work equally as well. Notice, no matter how wide the parent container becomes, the section and aside margins and widths scale proportionally.
```css
section,
aside {
  margin: 1.858736059%; /*  10px ÷ 538px = .018587361 */
}
section {
  float: left;
  width: 63.197026%;    /* 340px ÷ 538px = .63197026 */   
}
aside {
  float: right;
  width: 29.3680297%;  /* 158px ÷ 538px = .293680297 */
}
```
* Taking the flexible layout concept, and formula, and reapplying it to all parts of a grid will create a completely dynamic website, scaling to every viewport size. For even more control within a flexible layout, you can also leverage the min-width, max-width, min-height, and max-height properties.
* The flexible layout approach alone isn’t enough. At times the width of a browser viewport may be so small that even scaling the the layout proportionally will create columns that are too small to effectively display content. Specifically, when the layout gets too small, or too large, text may become illegible and the layout may begin to break. In this event, media queries can be used to help build a better experience.
# Media Queries
* Media queries were built as an extension to media types commonly found when targeting and including styles. Media queries provide the ability to specify different styles for individual browser and device circumstances, the width of the viewport or device orientation for example. Being able to apply uniquely targeted styles opens up a world of opportunity and leverage to responsive web design.
## Initializing Media Queries
* There are a couple different ways to use media queries, using the @media rule inside of an existing style sheet, importing a new style sheet using the @import rule, or by linking to a separate style sheet from within the HTML document. Generally speaking it is recommend to use the @media rule inside of an existing style sheet to avoid any additional HTTP requests.
```html
<link href="styles.css" rel="stylesheet" media="all and (max-width: 1024px)">
```
```css
@media all and (max-width: 1024px) 
@import url(styles.css) all and (max-width: 1024px)
```
## Logical Operators in Media Queries
* Logical operators in media queries help build powerful expressions. There are three different logical operators available for use within media queries, including and, not, and only.
* Using the and logical operator within a media query allows an extra condition to be added, making sure that a browser or devices does both a, b, c, and so forth. Multiple individual media queries can be comma separated, acting as an unspoken or operator. The example below selects all media types between 800 and 1024 pixels wide.
```html
@media all and (min-width: 800px) and (max-width: 1024px)
```
* The not logical operator negates the query, specifying any query but the one identified. In the example below the expression applies to any device that does not have a color screen. Black and white or monochrome screens would apply here for example.
```css
@media not screen and (color)
```
* The only logical operator is a new operator and is not recognized by user agents using the HTML4 algorithm, thus hiding the styles from devices or browsers that don’t support media queries. Below, the expression selects only screens in a portrait orientation that have a user agent capable of rending media queries.
