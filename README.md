
Zenponsive 
==========
A simple responsive CSS framework
----------------------------
Yet another framework ;-). This was primarily made to provide a plain simple and flexible fluid grid system for my own use (and education). It of course does not reinvent the wheel and is on purpose not trying to be a full design framework like the big ones. Those are great and were of course an inspiration but also a bit overloaded to my taste even if largely modular. 

**License**: GPL v3
 
Features
---------
- **Fluid scaling grid:** Percent based 12 column layout with predefined widths 960/1024/1280/1600/fullwidth (float based).
- **Prefixed id/class names:** All id or class names of Zenponsive are prefixed with `zp-` to be easily recognizable between custom css. *Note: There is still a `zenponsive-noprefixes.css` included that is considered deprecated now.*
- **No predefined styles and typography**: All styling up to you.
- **No JS involved**: 16 kb weight (uncompressed).
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
      <title>Zenponsive - A responsive CSS framework</title>
      <meta charset="UTF-8">
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

There are four predefined site widths to choose from:

- `.zp-w960` – Standard desktop width
- `.zp-w1280` – Bigger desktop width
- `.zp-w1600` – Big desktop width
- `.zp-wFull` – Full browser window width

You can use any size you wish for the main wrapper, too

See the `zenponsive.css` file for the file comments for more info. We use `zp-w960` here and six columns:

```html
<div id="zp-site" class="zp-w960">
  <div class="zp-col02"><h3>zp-col02</h3></div>
  <div class="zp-col02"><h3>zp-col02</h3></div>
  <div class="zp-col02"><h3>zp-col02</h3></div>
  <div class="zp-col02"><h3>zp-col02</h3></div>
  <div class="zp-col02"><h3>zp-col02</h3></div>
  <div class="zp-col02"><h3>zp-col02</h3></div>
</div>
```
    
By default all zp-columns become .`zp-col12` on 479px width and below and are just scaled on all other sizes. You can of course also nest columns within each other.

Don't set margins, borders or paddings on the columns class elements as that will disturb the layout calculation completely (it might work in newer browsers because it is using `box-sizing: border-box`). Set those on the elements within the columns instead.

Rows/wrapping zp-columns
----------------------
You don't need to wrap columns in rows. If your columns are the same size you can have for example two rows of six `.zp-col02` (e.g. a thumbnail gallery grid) you don't need to wrapp each row of six. You just need to wrap them all within `.zp-clearfix` to clear the floating on anything after them (e.g. another section of content).

```html
<div id="zp-site" class="zp-w960">
  <div class="zp-clearfix">
  <div class="zp-col02"><h3>zp-col02</h3></div>
  <div class="zp-col02"><h3>zp-col02</h3></div>
  <div class="zp-col02"><h3>zp-col02</h3></div>
  <div class="zp-col02"><h3>zp-col02</h3></div>
  <div class="zp-col02"><h3>zp-col02</h3></div>
  <div class="zp-col02"><h3>zp-col02</h3></div>
  <div class="zp-col02"><h3>zp-col02</h3></div>
  <div class="zp-col02"><h3>zp-col02</h3></div>
  <div class="zp-col02"><h3>zp-col02</h3></div>
  <div class="zp-col02"><h3>zp-col02</h3></div>
  <div class="zp-col02"><h3>zp-col02</h3></div>
  <div class="zp-col02"><h3>zp-col02</h3></div>
  </div>
  <p>Some other content</p>
</div>
```

However if you have several rows of columns and each column is not the same height as with e.g. thumbnails you need to wrap them to reset the floating so they appear as intended and not disturb the following rows.

```html
<div id="zp-site" class="zp-w960">
  <div class="zp-clearfix">
    <div class="zp-col02"><h3>zp-col02</h3></div>
    <div class="zp-col02"><h3>zp-col02</h3></div>
    <div class="zp-col02"><h3>zp-col02</h3></div>
    <div class="zp-col02"><h3>zp-col02</h3></div>
    <div class="zp-col02"><h3>zp-col02</h3></div>
    <div class="zp-col02"><h3>zp-col02</h3></div>
  </div>
  <div class="zp-clearfix">
    <div class="zp-col02"><h3>zp-col06</h3></div>
    <div class="zp-col08"><h3>zp-col06</h3></div>
  </div>
</div>
````

If your columns for example have background zp-color and need to really align visually on the right side, you should wrapp them within the `.zp-row` instead of `.zp-clearfix`.

```html
<div id="zp-site" class="zp-w960">
  <div class="zp-row">
    <div class="zp-col02"><h3>zp-col02</h3></div>
    <div class="zp-col02"><h3>zp-col02</h3></div>
    <div class="zp-col02"><h3>zp-col02</h3></div>
    <div class="zp-col02"><h3>zp-col02</h3></div>
    <div class="zp-col02"><h3>zp-col02</h3></div>
    <div class="zp-col02"><h3>zp-col02</h3></div>
  </div>
  <div class="zp-clearfix">
    <div class="zp-col02"><h3>zp-col06</h3></div>
    <div class="zp-col08"><h3>zp-col06</h3></div>
  </div>
</div>
````

`.zp-row` does basically the same as `.zp-clearfix` but it additionally floats the last item of a row to the right. This is because of pixel rounding issues of certain browsers. You should only use this with one row and if the columns add up to 12.

Sadly the `:last-child` CSS selector is not supported on every browser so you might need to add the class `.zp-floatright` manually to the last row item. This exists for all breakpoints predefined:

- `.zp-floatright` (Default)
- `.zp-floatright959`
- `.zp-floatright767`
- `.zp-floatright479`

An example: 

```html
<div id="zp-site" class="zp-w960">
  <div class="zp-row">
    <div class="zp-col02"><h3>zp-col02</h3></div>
    <div class="zp-col02"><h3>zp-col02</h3></div>
    <div class="zp-col02"><h3>zp-col02</h3></div>
    <div class="zp-col02"><h3>zp-col02</h3></div>
    <div class="zp-col02"><h3>zp-col02</h3></div>
    <div class="zp-col02 zp-floatright"><h3>zp-col02</h3></div>
  </div>
  <div class="zp-row">
    <div class="zp-col06"><h3>zp-col06</h3></div>
    <div class="zp-col06 zp-floatright"><h3>zp-col06</h3></div>
  </div> 
</div>
```       

Don't use `.zp-row` on `.zp-col12` elements.

Changing zp-columns
-----------------

###Changing even columns to even columns
But you can also request to turn any column to another column width using the special classes `.zp-colXX-959`/`.zp-colXX-767`/`.zp-colXX-479`. You can use these even to apply to be mobile first. Here an example that turns a `.zp-col02` (six per row) into `.zp-col04` (two times three per row) on the 767px breakpoint:

```html
<div id="zp-site" class="zp-w960">
  <div class="zp-col02 zp-col04-767"><h3>zp-col02</h3></div>
  <div class="zp-col02 zp-col04-767"><h3>zp-col02</h3></div>
  <div class="zp-col02 zp-col04-767"><h3>zp-col02</h3></div>
  <div class="zp-col02 zp-col04-767"><h3>zp-col02</h3></div> 
  <div class="zp-col02 zp-col04-767"><h3>zp-col02</h3></div>
  <div class="zp-col02 zp-col04-767"><h3>zp-col02</h3></div>
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
<div id="zp-site" class="zp-w960">
  <div class="zp-col02 zp-col03-767"><h3>zp-col02</h3></div>
  <div class="zp-col02 zp-col03-767"><h3>zp-col02</h3></div>
  <div class="zp-col02 zp-col03-767"><h3>zp-col02</h3></div>
  <!-- First of the 2nd row on 767px breakpoint -->
  <div class="zp-col02 zp-col03-767 floatclear767"><h3>zp-col02</h3></div>  
  <div class="zp-col02 zp-col03-767"><h3>zp-col02</h3></div>
  <div class="zp-col02 zp-col03-767 zp-floatright"><h3>zp-col02</h3></div>
</div>
````
    
Note the floatclear of the breakpoints before the current one are reseted to `clear: none`. That means if you wish to clear floating on several breakpoints the same way you need to assign the classes in order like this:

```html
<div id="zp-site" class="zp-w960">
  <div class="zp-col02 zp-col03-767"><h3>zp-col02</h3></div>
  <div class="zp-col02 zp-col03-767"><h3>zp-col02</h3></div>
  <div class="zp-col02 zp-col03-767"><h3>zp-col02</h3></div>
  <div class="zp-col02 zp-col03-767 floatclear floatclear959 floatclear767"><h3>zp-col02</h3></div>
  <div class="zp-col02 zp-col03-767"><h3>zp-col02</h3></div>
  <div class="zp-col02 zp-col03-767 zp-floatright"><h3>zp-col02</h3></div>
</div>
```
    
Change float order
------------------
All columns are set to `float:left`. Sometimes you may wish to change the order so you can request to `float:right` as well using the special classes (you saw one already above on the rows):

- `.zp-floatright` (initial size)
- `.zp-floatright959`
- `.zp-floatright767`
- `.zp-floatright479`

Example: 

```html
<div id="zp-site" class="zp-w960">
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
- `.zp-invisble`/`.zp-invisible979`/`.zp-invisible767`/`.zp-invisible479` (`visibility:hidden`)
- `.zp-visible`/`.zp-visible979`/`.zp-visible767`/`.zp-visible479` (`visibility:visible`)

This is especially usefull for clearing column floats on different breakpoints, e.g. after four on 767px width and two on 479px width.

Gutter
------
There are two predefined gutters available 2% and 4%. Just wrap the colums you wish to use with the gutter with one of these classes: 
- `.zp-gutter2`
- `.zp-gutter4`

The gutter is applied to the direct children only and uses negative left margins to achieve it. Don't use the gutter classes on a direct parent that has a `.zp-colXXX` class assigned but an additional wrapper. The negative margin otherwise can cause wrong display.

```html
<div id="zp-site" class="zp-w960">
  <div class="zp-row zp-gutter4">
    <div class="zp-col02"><h3>zp-col02</h3></div>
    <div class="zp-col02"><h3>zp-col02</h3></div>
    <div class="zp-col02"><h3>zp-col02</h3></div>
    <div class="zp-col02"><h3>zp-col02</h3></div>
    <div class="zp-col02"><h3>zp-col02</h3></div>
    <div class="zp-col02"><h3>zp-col02</h3></div>
  </div>
</div>
```

Demos
-----
To be added later.

TODO
----
- Extra version useing `flexbox` for modern browsers possibly
