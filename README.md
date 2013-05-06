Zenponsive 
==========
A simple responsive CSS framework with (Zenphoto) gallery themes in mind
----------------------------
Yes, just another framework ;-) Admittedly this is not that different from lots of other grid frameworks like bootstrap and of course is inspired by them. Why reinvent the wheel? 

Probably it is a bit less sophisticated than those. But I was made for my own use (and education) to provide a simple and flexible grid without all the bells and whistles others have to leave more freedom. 

*License: GPL v2 or later (zenponsive.css)*

*The separate and optional included [normalize.css - MIT license](http://necolas.github.io/normalize.css/http://necolas.github.io/normalize.css/)*

The features:
-------------

1. Fluid scaling percent based 12 column layout with predefined widths 960/1280/1600/fullwidth. 

2. No gutter by default: That way you can easily combine or nest columns around without needing to care about different left, middle or right margins for the first or last column in a row. You just set any margin/padding using your elements within the column using an custom css file. More freedom to you.

3. No predefined styles and typography: All styling up to you. Only a normalize css to reset browser differences is included.

4. Only three default mediaquery breakpoints on 980/767/479 since the framework is fully fluid. You can easily extend if you need or want more via your custom css file.

5. Extra column classes: By default all columns becomme full width (col12) on the smallest 479 breakpoint. But there are extra ones for some columns to force a different behaviour.

Browser support
----------------
Generally tested with latest browser versions of:
- Safari
- Firefox
- Opera
- Chrome
- IE7+ (responsiveness not directly tested).

Because of the percentage roundings are different in all browsers it may not always be 100% accurat (works best in Firefox and Chrome which perform subpixel rounding)

Demos
--------
See the demos on http://zenponsive.maltem.de
Also included in the package.

Setup
------------
This is quite simple:

	<!DOCTYPE html>
		<html>
			<head>
				<title>Zenponsive - A responsive CSS framework</title>
				<meta http-equiv="content-type" content="text/html; charset=UTF-8" />
				<meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1" />
		
				<!-- normalize.css v2.1.0 | MIT License | git.io/normalize - optional but recommended -->	
				<link rel="stylesheet" href="normalize.css" type="text/css" />
		
				<!-- The base responsive grid - required -->
				<link rel="stylesheet" href="../zenponsive.css" type="text/css" />
				
				<!-- Hacks so the clear classes work correctly on older IEs - optional -->
				<!--[if lt IE 7 ]><link rel="stylesheet" href="zenponsive-iehacks.css" type="text/css" /><![endif]-->
		
				<!-- Optional Custom CSS - name as you like - optional but makes sense, doesn't it? ;-) -->
				<link rel="stylesheet" href="custom.css" type="text/css" />
			</head>
		<body>
	
		<!-- Your stuff here -->
	
		</body>
 	</html>

That's all.

Example 1
-------------
A row of six col2 columns

    <div class="site" class="w960">
    	<div class="col02"><h3>col02</h3></div>
    	<div class="col02"><h3>col02</h3></div>
    	<div class="col02"><h3>col02</h3></div>
    	<div class="col02"><h3>col02</h3></div>
    	<div class="col02"><h3>col02</h3></div>
    	<div class="col02"><h3>col02</h3></div>
    </div>

By default all columns become col12 on 479 width and are just scaled on all other size.
You can of course also nest columns within each other. 

Example 2
-------------

If you have several rows of columns you need to wrap them to reset the floating so they appear as intended and not disturb the row:

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
    		<div class="col06"><h3>col06</h3></div>
    		<div class="col06"><h3>col06</h3></div>
    	</div>
  	</div>

To get a kind of gutter or padding, don't set that on the column but on the elements within.

Example 3
-----------

But you can also request to turn any column to another column width using the special classes `xxx-979`/`xxx-767`/`xxx-479`.
Her an example that turns a col02 into col04 on the 767 breakpoint:

    <div class="col02 col04-767"><img src="thumb.jpg" /></div>
    
If you need more breakpoints you can define them in your additional custom.css file.

Example 4
-------------

You can also put columns into a wrapper and change their behaviour col2 columns within a wrapper using the `xxx-xxx-n` classes.

    <div class="site" class="w960">
    	<div class="col04-767-n col06-479-n">
    		<div class="col02"><img src="thumb.jpg" /></div>
    		<div class="col02"><img src="thumb.jpg" /></div>
    		<div class="col02"><img src="thumb.jpg" /></div>
    		<div class="col02"><img src="thumb.jpg" /></div>
    		<div class="col02"><img src="thumb.jpg" /></div>
    		<div class="col02"><img src="thumb.jpg" /></div>
    	</div>
    </div>
    
This sets the col02 within the wrapper to col04 on `767px` width using the class `col04-767-n` and to col06 on `479px` width using the class `col06-479-n`.

Example 5
-------------
All columns are set to `float: left`. Sometimes you maybe wish to change the order so you can request to `float: right` as well using the special classes `.floatright-979/.floatright-767/.floatright-479`:

	 <div class="col02 col04-767 floatright-767"><img src="thumb.jpg" /></div>

