Zenponsive 
==========
A simple responsive CSS framework with (Zenphoto) gallery themes in mind
----------------------------
Or just another framework..;-) Admittedly this is not that different from lots of other grid frameworks and probably a bit less sophisticated. 

It was made to be a simple grid without all the bells and whistles others have to leave more freedom. 

*License: GPL v2 or later (zenponsive.css only – normalize.css is MIT licensed and not by me) *

The features:
-------------

1. Fluid scaling percent based 12 column layout (predefined widths 960/1280/1600/fullwidth). 

2. No gutter on purpose: That way you can easily combine or nest columns around without needing to care about different left, middle or right margins for the first or last column in a row. You just set any margin/padding using your elements within the column using an custom css file. More freedom to you.

3. No predefined styles and typography: All styling up to you. Only a normalize css to reset browser differences is included.

4. Only three default mediaqueries 980/767/479 since the framework is fully fluid. You can easily extend if you need or want more via your custom css file.

5. Extra column classes: By default all columns becomme full width (col12) on the smallest view. But there are extra ones for some columns to force different behaviour.

Browser support
----------------
Generally tested with latest browser versions of:
- Safari
- Firefox
- Opera
- Chrome
- IE7+ (responsiveness not directly tested).

Because of the percentage roundings are different in all browsers it may not always be 100% accurat (works best in Firefox and Chrome which perform subpixel rounding)

Code examples
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

By default all columns become col12 on 479 and are just scaled on all other size.
You can of course also nest columns within each other.

To get a kind of gutter or padding, don't set that on the column but on the elements within.

But you can also request to turn any column to another column width using the special classes `xxx-979`/`xxx-767`/`xxx-479`.

    <div class="col02 col04-767"><img src="thumb.jpg" /></div>
    
If you need more breakpoints you can define them in your additional custom.css file.


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


