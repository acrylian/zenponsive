zenponsive
==========

A simple responsive CSS framework with (Zenphoto) gallery themes in mind

Admittedly this is not that different from lots of other grid frameworks and probably a bit less sophisticated. 
It was made to be a simple grid that has no predefined design styles. 

The features:
-------------

1. Fluid scaling percent based 12 column layout (predefined width 960/1280/1600/fullwidth). 

2. No gutter on purpose: That way you can easily combine or nest columns around without needing to care about different left, middle or right margins for the first or last column in a row. You just set any margin/padding using your elements within the column using an custom css file. More freedom to you.
(note due percentage rounding differences the grid is not exact and the same on all browsers).

3. No predefined styles and typography: All styling up to you. Only a normalize css to eliminate browser differences is included

4. Only three default mediaqueries 980/767/479 since the framework is fully fluid. You can easily extend if you need or want more via your custom css file.

5. Extra column classes: By default all columns becomme full width (col12) on the smallest view. But there are extra ones for some columns to force different behaviour.


Browser support
----------------

Generally tested with latest 
- Safari
- Firefox
- Opera
- Chrome
- IE7+ (responsiveness not drictly tested).

Because of the percentage roundings is different in all browsers it may not always be 100% accurat (works best in

Code examples
-------------
Code example

A row of col2 columns
    <div class="site" class="w960">
    <div class="col02"><h3>col02</h3></div>
    <div class="col02"><h3>col02</h3></div>
    <div class="col02"><h3>col02</h3></div>
    <div class="col02"><h3>col02</h3></div>
    <div class="col02"><h3>col02</h3></div>
    <div class="col02"><h3>col02</h3></div>
    </div>


col2 columbs with a wrapper that sets them to col04 on 767px widht and to col06 on 479px width.

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


You can also set any column to that behaviour using the classes without "-n".

    <div class="col02 col04-767"><img src="thumb.jpg" /></div>
