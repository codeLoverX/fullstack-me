<h1> Spacing </h1>

<h3> Margin </h3>

<h5> CSS application </h5>
 
As name suggests

<h5> Classes </h5>

space-x-0 :	margin-left: 0px;
space-y-0 : margin-top: 0px;

1) 1 pixel: { margin: 1px } m[ -/x/y/t/b/l/r ]-px  

e.g. m-px, mx-px, my-px, mt-px, mb-px, ml-px, mr-px

2) in rem: m[ -/x/y/t/b/l/r ]-0

e.g. m-6, mx-6, my-6, mt-6, mb-6, ml-6, mr-6

3) in auto: m[ -/x/y/t/b/l/r ]-auto 

e.g. m-auto, mx-auto, my-auto, mt-auto, mb-auto, ml-auto, mr-auto

<h5> Using negative values </h5>

To use a negative space value, prefix the class name with a dash to convert it to a negative value.

-m[ -/x/y/t/b/l/r ]-auto 

e.g. 
-m-auto; 
-mx-auto, -my-auto, -mt-auto, -mb-auto, -ml-auto, -mr-auto;
-m-px -m[ x/y/t/b/r/l ]-px ; -m-0 -m[ x/y/t/b/r/l ]-0

<h3> Padding </h3>

<h5> CSS application </h5>
 
As name suggests

<h5> Classes </h5>

1) 1 pixel: { padding: 1px }

p[ -/x/y/t/b/l/r ]-px 

e.g. p-px, px-px, py-px, pt-px, pb-px, pl-px, pr-px

2) rem: 

p[ -/x/y/t/b/l/r ]-[0...96 ]   

e.g. p-6, px-6, py-6, pt-6, pb-6, pl-6, pr-6

<h5> Using negative values </h5>

>>> Negative values of padding are not allowed! 

a) Inside tailwind.config.js file, you can extend Tailwind with your own custom utility classes where you can easily add a custom class something like

neg-m-16:{margin:-1rem}

b) You can write your custom value like this even negative value too,

py-[-30px] mx-[-20px] translate-y-[-50%] translate-x-[-50%]

<h3> Margin </h3>

<h3> Space </h3>

Tailwind always suggests left  and top, not right and bottom margin. 

<h5> CSS application </h5>

* space-x is for margin-left; space-y is for margin-top  

space-x-0 :	margin-left: 0px; space-y-0 : margin-top: 0px;

<h5> Classes </h5>

1) 1 pixel: means 1px 


space-x-px space-y-px 

2) rem: space-x-[0...96 ] space-y-[0...96 ]  

e.g. space-x-6, space-y-6,
