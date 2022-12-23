
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

<pre>
&ltdiv class="w-[32rem]"> 
  &lt!-- ... -->
&lt/div>
</pre>

<h1> Customization </h1>

You can customize your min-height scale by editing theme.minHeight or theme.extend.minHeight in your tailwind.config.js file.

tailwind.config.js
<pre>
module.exports = {
  theme: {
    minHeight: {
      '1/2': '50%',
    }
  }
}
</pre>

Arbitrary values
If you need to use a one-off value that doesn’t make sense to include in your theme, use square brackets to generate a property on the fly using any arbitrary value.

<pre>
&ltdiv class="min-h-[50%]"> 
  &lt!-- ... -->
&lt/div>
</pre>

