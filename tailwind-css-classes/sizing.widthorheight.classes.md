* to learn moore about w-[ 0...96 ]/ h-[ 0...96 ]  go to spacing.margin.classes.md

<h1> This supports 6 types of class </h1>

1) in pixels <br>
px means 1px <br>
w-px h-px 

2) in rem <br>
w-[ 0...96 ] h-[ 0...96 ] 

3) content: mix, max, fit <br>
w-min, w-max, w-fit / h-min, h-max, h-fit

4) full-screen <br>
w-screen

5) percentage <br>
w-1/12, w-2/12, w-3/12,  ... w-11/12, w-full / <br>
h-1/12, h-2/12, h-3/12,  ... h-11/12, h-full   

6) auto width <br>
w-auto / h-auto

<h1> Customization </h1>

You can customize your spacing scale by editing theme.spacing or theme.extend.spacing in your tailwind.config.js file.
To customize width separately, use the theme.width section of your tailwind.config.js file.

tailwind.config.js
<pre>
module.exports = {
  theme: {
    extend: {
      spacing/width/height: {
        '128': '32rem',
      }
    }
  }
}
</pre>

Arbitrary values
If you need to use a one-off width value that doesn’t make sense to include in your theme, use square brackets to generate a property on the fly using any arbitrary value.

<code>
\<div class="w-[32rem]">
  <!-- ... -->
\</div>
</code>

