
Zenponsive 
==========
A simple responsive CSS framework
----------------------------
Yet another framework ;-) 
---------------------------
This was primarily made to provide a plain simple and flexible fluid grid system for my own use (and education). It is on purpose not trying to be a full design framework like Bootstrap, Foundation, YAML etc. that are great and were of course an inspiration. But those are a bit overloaded even if largely modular to my taste.

**License**: GPL v3*
 
Features
---------
- Fluid scaling percent based 12 column layout with predefined widths 960/1024/1280/1600/fullwidth (float based).
- No predefined styles and typography. All styling up to you.
- No JS involved and 17 kb weight (uncompressed).
- Only three default mediaquery breakpoints on Full/959/767/479px widths. You can easily extend if you need or want more via your custom css file.
- Extra column classes: By default all columns become full width (col12) on the smallest 479 breakpoint. But there are extra classes to force a different behaviour on certain breakpoints.

Browser support
---------------
Generally aimed at modern browsers :-)

Setup
-----
This is quite simple:

    <!DOCTYPE html>
      <html>
        <head>
          <title>Zenponsive - A responsive CSS framework</title>
          <meta charset="UTF-8">
          <meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1">
          <!-- normalize.css v2.1.0 | MIT License | git.io/normalize - optional but recommended to include -->   
          <link rel="stylesheet" href="normalize.css" type="text/css" />
          <!-- The responsive grid - required -->
          <link rel="stylesheet" href="zenponsive.css" type="text/css" />
          <!-- Hacks so the clear classes work correctly on older IEs - really optional -->
          <!--[if lt IE 7 ]><link rel="stylesheet" href="zenponsive-iehacks.css" type="text/css" /><![endif]-->
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
    
That's all. Of course you can also combine all css into one to speed up loading.
    
Basic structure
----------------
There are four predefined site widths to choose from:

- `.w960` – Standard desktop width
- `.w1280` – Bigger desktop width
- `.w1600` – Big desktop width
- `.wFull` – Full browser window width

You can use any size you wish for the main wrapper, too

See the `zenponsive.css` file for the file comments for more info. We use `w960` here and six columns:

    <div class="site" class="w960">
      <div class="col02"><h3>col02</h3></div>
      <div class="col02"><h3>col02</h3></div>
      <div class="col02"><h3>col02</h3></div>
      <div class="col02"><h3>col02</h3></div>
      <div class="col02"><h3>col02</h3></div>
      <div class="col02"><h3>col02</h3></div>
    </div>
    
By default all columns become .`col12` on 479px width and below and are just scaled on all other sizes. You can of course also nest columns within each other.

Don't set margins, borders or paddings on the columns class elements as that will disturb the layout calculation completely (it might work in newer browsers because it is using `box-sizing: border-box`). Set those on the elements within the columns instead.

Rows/wrapping columns
----------------------
You don't need to wrap columns in rows. If your columns are the same size you can have for example two rows of six `.col02` (e.g. a thumbnail gallery grid) you don't need to wrapp each row of six. You just need to wrap them all within `.clearfix` to clear the floating on anything after them (e.g. another section of content).

    <div class="site" class="w960">
      <div class="clearfix">
        <div class="col02"><h3>col02</h3></div>
        <div class="col02"><h3>col02</h3></div>
        <div class="col02"><h3>col02</h3></div>
        <div class="col02"><h3>col02</h3></div>
        <div class="col02"><h3>col02</h3></div>
        <div class="col02"><h3>col02</h3></div>
        <div class="col02"><h3>col02</h3></div>
        <div class="col02"><h3>col02</h3></div>
        <div class="col02"><h3>col02</h3></div>
        <div class="col02"><h3>col02</h3></div>
        <div class="col02"><h3>col02</h3></div>
        <div class="col02"><h3>col02</h3></div>
      </div>
      <p>Some other content</p>
    </div>

However if you have several rows of columns and each column is not the same height as with e.g. thumbnails you need to wrap them to reset the floating so they appear as intended and not disturb the following rows.

    <div class="site" class="w960">
      <div class="clearfix">
        <div class="col02"><h3>col02</h3></div>
        <div class="col02"><h3>col02</h3></div>
        <div class="col02"><h3>col02</h3></div>
        <div class="col02"><h3>col02</h3></div>
        <div class="col02"><h3>col02</h3></div>
        <div class="col02"><h3>col02</h3></div>
      </div>
      <div class="clearfix">
        <div class="col02"><h3>col06</h3></div>
        <div class="col08"><h3>col06</h3></div>
      </div>
    </div>
    

If your columns for example have background color and need to really align visually on the right side, you should wrapp them within the `.row` instead of `.clearfix`.

    <div class="site" class="w960">
      <div class="row">
        <div class="col02"><h3>col02</h3></div>
        <div class="col02"><h3>col02</h3></div>
        <div class="col02"><h3>col02</h3></div>
        <div class="col02"><h3>col02</h3></div>
        <div class="col02"><h3>col02</h3></div>
        <div class="col02"><h3>col02</h3></div>
      </div>
      <div class="clearfix">
        <div class="col02"><h3>col06</h3></div>
        <div class="col08"><h3>col06</h3></div>
      </div>
    </div>

`.row` does basically the same as `.clearfix` but it additionally floats the last item of a row to the right. This is because of pixel rounding issues of certain browsers. You should only use this with one row and if the cols add up to 12.

Sadly the `:last-child` CSS selector is not supported on every browser so you might need to add the class `.floatright` manually to the last row item. This exists for all breakpoints predefined:

- `.floatright` (Default)
- `.floatright959`
- `.floatright767`
- `.floatright479`

An example: 

     <div class="site" class="w960">
       <div class="row">
         <div class="col02"><h3>col02</h3></div>
         <div class="col02"><h3>col02</h3></div>
         <div class="col02"><h3>col02</h3></div>
         <div class="col02"><h3>col02</h3></div>
         <div class="col02"><h3>col02</h3></div>
         <div class="col02 floatright"><h3>col02</h3></div>
       </div>
       <div class="row">
         <div class="col06"><h3>col06</h3></div>
         <div class="col06 floatright"><h3>col06</h3></div>
       </div> 
     </div>
       

Don't use `.row` on `.col12` elements.

Changing columns
-----------------

###Changing even columns to even columns)
But you can also request to turn any column to another column width using the special classes `.colXX-959`/`.colXX-767`/`.colXX-479`. You can use these even to apply to be mobile first. Here an example that turns a `.col02` (six per row) into `.col04` (two times three per row) on the 767px breakpoint:

    <div class="site" class="w960">
      <div class="col02 col04-767"><h3>col02</h3></div>
      <div class="col02 col04-767"><h3>col02</h3></div>
      <div class="col02 col04-767"><h3>col02</h3></div>
      <div class="col02 col04-767"><h3>col02</h3></div> 
      <div class="col02 col04-767"><h3>col02</h3></div>
      <div class="col02 col04-767"><h3>col02</h3></div>
    </div>
    
If you need more breakpoints you can define them in your additional `custom.css` file.

###Changing even columns to even (and vice versa) without rows
You can also work without an extra `.row` or a `.clearfix` wrapper. If you use breakpoints switch to different columns on different breakpoints and the column height is not the same (e.g. not square thumbs), the wrapper gets into your way as the row does not fit anymore. For example if you start with six `.col02` and switch to `.col03` you will get two rows.

In this case use the `.floatclearXXX` classes on the first row item of the 2nd and onward rows. This exists for all four default breakpoints so you can address the rows individually:

- `.floatclear` (just a `clear: both`)
- `.floatclear959`
- `.floatclear767`
- `.floatclear479`

Example:

    <div class="site" class="w960">
      <div class="col02 col03-767"><h3>col02</h3></div>
      <div class="col02 col03-767"><h3>col02</h3></div>
      <div class="col02 col03-767"><h3>col02</h3></div>
      <!-- First of the 2nd row on 767px breakpoint -->
      <div class="col02 col03-767 floatclear767"><h3>col02</h3></div>  
      <div class="col02 col03-767"><h3>col02</h3></div>
      <div class="col02 col03-767 floatright"><h3>col02</h3></div>
    </div>
    
Note the floatclear of the breakpoints before the current one are reseted to `clear: none`. That means if you wish to clear floating on several breakpoints the same way you need to assign the classes in order like this:

    <div class="site" class="w960">
      <div class="col02 col03-767"><h3>col02</h3></div>
      <div class="col02 col03-767"><h3>col02</h3></div>
      <div class="col02 col03-767"><h3>col02</h3></div>
      <div class="col02 col03-767 floatclear floatclear959 floatclear767"><h3>col02</h3></div>
      <div class="col02 col03-767"><h3>col02</h3></div>
      <div class="col02 col03-767 floatright"><h3>col02</h3></div>
    </div>
    
Change float order
------------------
All columns are set to `float:left`. Sometimes you may wish to change the order so you can request to `float:right` as well using the special classes (you saw one already above on the rows):

- `.floatright` (initial size)
- `.floatright959`
- `.floatright767`
- `.floatright479`

Example: 

    <div class="site" class="w960">
      <div class="col02 floatright767"><img src="thumb.jpg" /></div>
      <div class="col010"><img src="thumb.jpg" /></div>
    </div>
    
This of course only works if you have at least two columns that actually float.

Hiding elements
---------------
General classes are available to hide elements initially and/or on breakpoints:

- `.hide`/`.hide979`/`.hide767`/`.hide479` (`display: none`)
- `.show`/`.show979`/`.show767`/`.show479` (`display: block`)
- `.invisble`/`.invisible979`/`.invisible767`/`.invisible479` (`visibility:hidden`)
- `.visible`/`.visible979`/`.visible767`/`.visible479` (`visibility:visible`)

This is especially usefull for clearing column floats on different breakpoints, e.g. after four on 767px width and two on 479px width.

Gutter
------
There are two predefined gutters available 2% and 4%. Just wrap the colums you wish to use with the gutter with one of these classes: 
- `.gutter2`
- `.gutter4`

The gutter is applied to the direct children only and uses negative left margins to achieve it. Don't use the gutter classes on a direct parent that has a `.colXXX` class assigned but an additional wrapper. The negative margin otherwise can cause wrong display.

    <div class="site" class="w960">
      <div class="row gutter4">
        <div class="col02"><h3>col02</h3></div>
        <div class="col02"><h3>col02</h3></div>
        <div class="col02"><h3>col02</h3></div>
        <div class="col02"><h3>col02</h3></div>
        <div class="col02"><h3>col02</h3></div>
        <div class="col02"><h3>col02</h3></div>
      </div>
    </div>

Demos
======
To be added later.

TODO
====
- Extra version useing `flexbox` for modern browsers possibly





