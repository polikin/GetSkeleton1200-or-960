GetSkeleton1200-or-960
======================

Sometimes the designer designs with the 960 grid and sometime with the 1200 grid . So, I decided to merge both grid into one single scss file. Then, you can call which grid you want with the $layout variable.

#####Example | file: _core-functions.scss
---
`@import "_responsive-grid";`  
`@include responsive($responsive);`

`$responsive: true;`  
`$layout: 1200;`

---

#####Fit the 1200 grid into 1024/1140 resolution for the "lovely" IE


Obviously, the 1200 width grid will not fit into 1024/1140 resolution with IE. The trick here is that we use an lightweight plugin call [syze](https://github.com/rezitech/syze) - http://rezitech.github.io/syze/

Why? Because, we can use some .js file like [css3-mediaqueries-js](https://github.com/rezitech/syze), but I prefered to use class to target breakpoint.

---

#####Implementation

 To use syze, include this script anywhere in your page.
 `<script src="//rezitech.github.com/syze/syze.min.js"></script>`

then 
`syze.sizes(320, 480, 760, 960, 1024, 1130, 1180).names({ 320:'320', 480:'480', 760:'768', 960:'960',`
`1024:'1024', 1130:'1140', 1180:'1200' });`

Voilà! IE will use the 960 grid. Maybe you will have to adjust your styles (menu, h1, h2, etc) to fit into this grid.

------

#####Mixin to use to fix your styles (SCSS)
------

`.selector {`  
  `font-size:15px;`    
  `@include ie-grid { font-size: 12px;``}`    
`}`

#####Enable & disable responsive (SCSS)
------

For X reasons, sometimes we don't have the budget to make the website responsive. So, you can still use the skeleton grid, but it will not be responsive.
The only thing you need is the variable $responsive.

true == load the grid with the media queries / false == load the base grid only

**Note: The variable $responsive must be included before the $layout variable**

`$responsive: true;`  
`layout: 1200;`


#####Tips
------

Wrap your content into `<div class="wrapper"></div>`
