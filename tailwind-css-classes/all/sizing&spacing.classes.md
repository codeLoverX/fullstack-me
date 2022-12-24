<h1> Spacing </h1>

<h2> Margin </h2>

<h3> CSS property </h3>
 
.m-px{ margin: 1px; } \
.mx-6{ margin-left: 6rem; margin-right: 6rem; } \
.my-auto{ margin-top: auto; margin-bottom: auto; } \
.-mr-6 { marigin-right: -6rem; } 

<h3> Classes </h3>

1) 1 pixel: { margin: 1px } m[ -/x/y/t/b/l/r ]-px  \
e.g. m-px, mx-px, my-px, mt-px, mb-px, ml-px, mr-px

2) in rem: m[ -/x/y/t/b/l/r ]-[0...96]  \property
e.g. m-6, mx-6, my-6, mt-6, mb-6, ml-6, mr-6

3) in auto: m[ -/x/y/t/b/l/r ]-auto   \property
e.g. m-auto, mx-auto, my-auto, mt-auto, mb-auto, ml-auto, mr-auto

<h3> Using negative values </h3>

To use a negative space value, prefix the class name with a dash to convert it to a negative value.

<!-- <h3> Limitations </h3>

Margin is not good for layouts like flex, grid. May use width and margin for entire flex, but gap is superior for each item. 
 -->

-m[ -/x/y/t/b/l/r ]-auto   \property
e.g. -m-auto; -m-px; -mx-6

<h2> Padding </h2>

<h3> CSS property </h3>
 
.p-px{ padding: 1px; }
.px-6{ padding-left: 6rem; padding-right: 6rem; }
.py-auto{ padding-top: auto; padding-bottom: auto; }
.-pr-6 { padding-right: -6rem; } 

<h3> Classes </h3>

1) 1 pixel: { padding: 1px }  p[ -/x/y/t/b/l/r ]-px   \property
e.g. p-px, px-px, py-px, pt-px, pb-px, pl-px, pr-px

2) rem: p[ -/x/y/t/b/l/r ]-[0...96 ]    \property
e.g. p-6, px-6, py-6, pt-6, pb-6, pl-6, pr-6

<h3> Using negative values </h3>

>>> Negative values of padding are not allowed! 

a) Inside tailwind.config.js file, you can extend Tailwind with your own custom utility classes where you can easily add a custom class something like \property
neg-m-16:{margin:-1rem}

b) You can write your custom value like this even negative value too  \property
py-[-30px] mx-[-20px] translate-y-[-50%] translate-x-[-50%]

<h2> Margin </h2>

<h2> Space </h2>

Tailwind always suggests left  and top, not right and bottom margin. 

<h3> CSS property </h3>

* space-x is for margin-left; space-y is for margin-top  \property  
space-x-0 {	margin-left: 0px }

.space-y-0 { margin-top: 0px; }

<h3> Classes </h3>

1) 1 pixel: means 1px  \property
e.g. space-x-px space-y-px 

2) rem: space-x-[0...96 ], space-y-[0...96 ]   \property
e.g. space-x-6, space-y-6,

<h3> Using negative values </h3>

>>> Same as margin class

<h3> Limitations </h3>

Not good for divide utilities (Utilities for controlling the border width between elements.)
