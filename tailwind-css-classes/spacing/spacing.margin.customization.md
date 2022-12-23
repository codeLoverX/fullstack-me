<h1> Theme customization </h1>

1) By default, Tailwind’s margin/ padding/ spacing scale uses the default spacing scale. You can customize your spacing scale by editing theme.spacing or theme.extend.spacing in your tailwind.config.js file.

tailwind.config.js
module.exports = {
  theme: {
    extend: {
      spacing: {
        '5px': '5px',
      }
    }
  }
}

2) Alternatively, you can customize just the margin scale by editing theme.margin or theme.extend.margin in your tailwind.config.js file.
For spacing and padding, editing theme.space or theme.extend.space

ailwind.config.js
module.exports = {
  theme: {
    extend: {
      margin/space/padding: {
        '5px': '5px',
      }
    }
  }
}

3) Arbitrary values
If you need to use a one-off margin value that doesn’t make sense to include in your theme, use square brackets to generate a property on the fly using any arbitrary value.

<div class="m-[5px]">
  <!-- ... -->
</div>
