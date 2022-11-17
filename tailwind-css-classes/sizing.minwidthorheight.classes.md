<h1> The height supports 6 classes, width doesn't </h1>

1. px <br>
min-h-0	             min-height: 0px; <br>
min-h-screen	     min-height: 100vh;

2. % <br>
min-h-full	         min-height: 100%;

3. min, max, fit <br>
min-h-min min-h-max  min-h-fit	

<h1> Theres is no min-w-screen </h1>
min-w-0	min-w-full min-w-min min-w-max  min-w-fit	<br>
Seems unnecessary, too! 

<h1> Application </h1>
min-width 
1. Sometimes if a container is too small its children will overflow <br>


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

