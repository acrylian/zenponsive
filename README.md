
Zenponsive 
==========
A simple responsive CSS grid
----------------------------
Yet another grid ;-) This was primarily made to provide a plain simple and flexible fluid grid system for my own use (and education). It of course does not reinvent the wheel and is on purpose not trying to be a full design framework like the big ones. Those are great and were of course an inspiration but also a bit overloaded to my taste even if largely modular. 

**License**: GPL v3
 
Features
---------
- **Fluid scaling grid:** Percent based 12 column layout with predefined widths 960/1024/1280/1600/fullwidth (float based).
- **Prefixed id/class names:** All id or class names of Zenponsive are prefixed with `zp-` to be easily recognizable between custom css. *Note: There is still a `zenponsive-noprefixes.css` included that is considered deprecated now.*
- **No predefined styles and typography**: All styling up to you.
- **No JS involved**: 17 kb weight (uncompressed).
- **Three default mediaquery breakpoints**: 959/767/479px widths. You can easily extend if you need or want more via your custom css file.
- **Extra column classes:** By default all columns become full width (`zp-col12`) on the smallest 479 breakpoint. But there are extra classes to force a different behaviour on certain breakpoints.

Browser support
---------------
Well, modern browsers but might work with IE9 :-)

Setup
-----
This is quite simple:

```html
<!DOCTYPE html>
  <html>
    <head>
      <title>Zenponsive - A responsive CSS grid</title>
      <meta charset="UTF-8">
      <meta http-equiv="X-UA-Compatible" content="IE=edge">
      <meta name="viewport" content="width=device-width, initial-scale=1">
      <!-- normalize.css v2.1.0 | MIT License | git.io/normalize - optional but recommended to include -->   
      <link rel="stylesheet" href="normalize.css" type="text/css" />
      <!-- The responsive grid - required -->
      <link rel="stylesheet" href="zenponsive.css" type="text/css" />
      <!-- https://github.com/aFarkas/html5shiv | Optional but recommended for older non HTML5 capable browsers -->
      <!--[if lt IE 9]>
        <script src="../html5shiv.js"></script>
        <script src="../html5shiv-printshiv.js"></script>
      <![endif]-->
      <!-- Optional Custom CSS - name as you like - optional but makes sense, doesn't it? ;-) -->
      <link rel="stylesheet" href="custom.css" type="text/css" />
    </head>
    <body>
      <!-- Your stuff here -->
    </body>
  </html>
```
    
That's all. Of course you can also combine all css into one to speed up loading.
    
Basic structure
----------------

###Prefefined widths

There are some predefined site widths you can use:

- `.zp-w479` – Mobile width
- `.zp-w767` – Tablet width
- `.zp-w960` – Standard desktop width
- `.zp-w1280` – Bigger desktop width
- `.zp-w1600` – Big desktop width
- `.zp-wFull` – Full browser window width

These just set a `max-width: XXXpx respectively `max-width: 100%` for `.zp-wFull`. Since the grid itself is percentage based you can of course use any other custom width.


###Columns

- `.zp-col01` to `.zp-col12`: By default all columns become `zp-col12 ´ on the 479px breakpoint
- `.zp-col01-959` to `.zp-col12-959`: Request a column change on the 960px breakpoint
- `.zp-col01-767` to `.zp-col12-767`: Request a column change on the 767px breakpoint
- `.zp-col01-479` to .zp-col12-479`: Request a column change on the 479px breakpoint

Here a basic example using `.zp-w960` here and six columns:

```html
<div id="zp-wrapper" class="zp-w960">
  <div class="zp-col02">zp-col02</div>
  <div class="zp-col02">zp-col02</div>
  <div class="zp-col02">zp-col02</div>
  <div class="zp-col02">zp-col02</div>
  <div class="zp-col02">zp-col02</div>
  <div class="zp-col02">zp-col02</div>
</div>

```
`.zp-wrapper` or for the main content`#zp-wrapper` is a general wrapper for the main content that is centered in the browser. Use it together with a width like `.zp-960`.
   
Avoid setting margins, borders or paddings on the columns class elements as that will disturb the layout calculation completely (it might work in newer browsers because it is using `box-sizing: border-box`). Set those on the elements within the columns instead.

Rows/wrapping zp-columns
----------------------
You don't need to wrap columns in rows. If your columns are the same size you can have for example two rows of six `.zp-col02` (e.g. a thumbnail gallery grid) you don't need to wrapp each row of six. You just need to wrap them all within `.zp-clearfix` to clear the floating on anything after them (e.g. another section of content). You can also use the alias `.zp-row`. 


```html
<div id="zp-wrapper" class="zp-w960">
  <div class="zp-clearfix">
  <div class="zp-col02">zp-col02</div>
  <div class="zp-col02">zp-col02</div>
  <div class="zp-col02">zp-col02</div>
  <div class="zp-col02">zp-col02</div>
  <div class="zp-col02">zp-col02</div>
  <div class="zp-col02">zp-col02</div>
  <div class="zp-col02">zp-col02</div>
  <div class="zp-col02">zp-col02</div>
  <div class="zp-col02">zp-col02</div>
  <div class="zp-col02">zp-col02</div>
  <div class="zp-col02">zp-col02</div>
  <div class="zp-col02">zp-col02</div>
  </div>
  <p>Some other content</p>
</div>
```

However if you have several rows of columns and each column is not the same height as with e.g. thumbnails you need to wrap them to reset the floating so they appear as intended and not disturb the following columns.

```html
<div id="zp-wrapper" class="zp-w960">
  <div class="zp-clearfix">
    <div class="zp-col02">zp-col02</div>
    <div class="zp-col02">zp-col02</div>
    <div class="zp-col02">zp-col02</div>
    <div class="zp-col02">zp-col02</div>
    <div class="zp-col02">zp-col02</div>
    <div class="zp-col02">zp-col02</div>
  </div>
  <div class="zp-clearfix">
    <div class="zp-col02">zp-col06</div>
    <div class="zp-col08">zp-col06</div>
  </div>
</div>
````


IF you have columns with background color you might encounter rounding issue in some browsers so that the last row column is not aligning correctly to the right. Use `.zp-floatright` manually to the last row item. This exists for all breakpoints predefined:

- `.zp-floatright` (Default size)
- `.zp-floatright959`
- `.zp-floatright767`
- `.zp-floatright479`

An example: 

```html
<div id="zp-wrapper" class="zp-w960">
  <div class="zp-row">
    <div class="zp-col02">zp-col02</div>
    <div class="zp-col02">zp-col02</div>
    <div class="zp-col02">zp-col02</div>
    <div class="zp-col02">zp-col02</div>
    <div class="zp-col02">zp-col02</div>
    <div class="zp-col02 zp-floatright">zp-col02</div>
  </div>
  <div class="zp-row">
    <div class="zp-col06">zp-col06</div>
    <div class="zp-col06 zp-floatright">zp-col06</div>
  </div> 
</div>
```       

Don't use `.zp-row` on `.zp-col12` elements. The float class of the previous breakpoint is reseted on the next to avoid unwanted clearing. So it also needs to be set for every breakpoint if needed.

Changing zp-columns
-----------------

###Changing even columns to even columns
But you can also request to turn any column to another column width using the special classes `.zp-colXX-959`/`.zp-colXX-767`/`.zp-colXX-479`. You can use these even to apply to be mobile first. Here an example that turns a `.zp-col02` (six per row) into `.zp-col04` (two times three per row) on the 767px breakpoint:

```html
<div id="zp-wrapper" class="zp-w960">
	<div class="zp-row">
  <div class="zp-col02 zp-col04-767">zp-col02</div>
  <div class="zp-col02 zp-col04-767">zp-col02</div>
  <div class="zp-col02 zp-col04-767">zp-col02</div>
  <div class="zp-col02 zp-col04-767">zp-col02</div> 
  <div class="zp-col02 zp-col04-767">zp-col02</div>
  <div class="zp-col02 zp-col04-767">zp-col02</div>
  </div>
</div>
```
    
If you need more breakpoints you can define them in your additional `custom.css` file.

###Changing even zp-columns to uneven (and vice versa) without rows
You can also work without an extra `.zp-row` or a `.zp-clearfix` wrapper. If you use breakpoints switch to different columns on different breakpoints and the column height is not the same (e.g. not square thumbs), the wrapper gets into your way as the row does not fit anymore. For example if you start with six `.zp-col02` and switch to `.zp-col03` you will get two rows.

In this case use the `.zp-floatclearXXX` classes on the first row item of the 2nd and onward rows. This exists for all four default breakpoints so you can address the rows individually:

- `.zp-floatclear` (just a `clear: both`)
- `.zp-floatclear959`
- `.zp-floatclear767`
- `.zp-floatclear479`

Example:

```html
<div id="zp-wrapper" class="zp-w960">
  <div class="zp-col02 zp-col03-767">zp-col02</div>
  <div class="zp-col02 zp-col03-767">zp-col02</div>
  <div class="zp-col02 zp-col03-767">zp-col02</div>
  <!-- First of the 2nd row on 767px breakpoint -->
  <div class="zp-col02 zp-col03-767 zp-floatclear767">zp-col02</div>  
  <div class="zp-col02 zp-col03-767">zp-col02</div>
  <div class="zp-col02 zp-col03-767 zp-floatright">zp-col02</div>
</div>
````
    
Note the floatclear of the breakpoints before the current one are reseted to `clear: none`. That means if you wish to clear floating on several breakpoints the same way you need to assign the classes in order like this:

```html
<div id="zp-wrapper" class="zp-w960">
  <div class="zp-col02 zp-col03-767">zp-col02</div>
  <div class="zp-col02 zp-col03-767">zp-col02</div>
  <div class="zp-col02 zp-col03-767">zp-col02</div>
  <div class="zp-col02 zp-col03-767 zp-floatclear">zp-col02</div>
  <div class="zp-col02 zp-col06-767 zp-floatclear767">zp-col02</div>
  <div class="zp-col02 zp-col06-767 zp-floatright">zp-col02</div>
</div>
```

Gutter
------
There are two predefined gutters available 2% and 4%. Just wrap the colums you wish to use with the gutter with one of these classes: 
- `.zp-gutter2`
- `.zp-gutter4`

The gutter is applied to the direct children only and uses negative left margins to achieve it. 

```html
<div id="zp-wrapper" class="zp-w960">
  <div class="zp-row zp-gutter4">
    <div class="zp-col02">zp-col02</div>
    <div class="zp-col02">zp-col02</div>
    <div class="zp-col02">zp-col02</div>
    <div class="zp-col02">zp-col02</div>
    <div class="zp-col02">zp-col02</div>
    <div class="zp-col02">zp-col02</div>
  </div>
</div>
```
Don't use the gutter classes on a direct parent that has a `.zp-colXXX` class assigned but an additional wrapper. The negative margin otherwise can cause wrong display.

Full width sites
----------------
Sometimes you may wish to have a full width colored or textured background on sections of your site but the actual content centered. To achieve this simply use a wrapper:

```html
<div id="zp-wrapper"><!-- full width -->
 <div class="zp-wFull"><!-- width: 100% if you have a wrapper, otherwise obsolete of course -->
  <div class="zp-row zp-gutter4">
    <div class="zp-col02">zp-col02</div>
    <div class="zp-col02">zp-col02</div>
    <div class="zp-col02">zp-col02</div>
    <div class="zp-col02">zp-col02</div>
    <div class="zp-col02">zp-col02</div>
    <div class="zp-col02">zp-col02</div>
  </div>
 </div>
</div>
```
Instead of the id `#zp-wrapper` you can also use the `.zp-wrapper` class.
    
Change float order
------------------
All columns are set to `float:left`. Sometimes you may wish to change the order so you can request to `float:right` as well using the special classes (you saw one already above on the rows):

- `.zp-floatright` (initial size)
- `.zp-floatright959`
- `.zp-floatright767`
- `.zp-floatright479`

Example: 

```html
<div id="zp-wrapper" class="zp-w960">
  <div class="zp-col02 zp-floatright767"><img src="thumb.jpg" /></div>
  <div class="zp-col010"><img src="thumb.jpg" /></div>
</div>
```
    
This of course only works if you have at least two zp-columns that actually float.

Hiding elements
---------------
General classes are available to hide elements initially and/or on breakpoints:

- `.zp-hide`/`.zp-hide979`/`.zp-hide767`/`.zp-hide479` (`display: none`)
- `.zp-show`/`.zp-show979`/`.zp-show767`/`.zp-show479` (`display: block`)
- `.zp-invisible`/`.zp-invisible979`/`.zp-invisible767`/`.zp-invisible479` (`visibility:hidden`)
- `.zp-visible`/`.zp-visible979`/`.zp-visible767`/`.zp-visible479` (`visibility:visible`)


Demos
-----
To be added later.

TODO
----
- Extra version useing `flexbox` for modern browsers possibly
