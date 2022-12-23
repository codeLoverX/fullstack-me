<h1> Customizing the default spacing and sizing scale for your project. </h1>

Use the spacing key in the theme section of your tailwind.config.js file to customize Tailwind’s default spacing/sizing scale.

<h3> One spacing unit is equal to 0.25rem, which translates to 4px by default in common browsers. </h3>

<h3> By default the spacing scale is inherited by the padding, margin, width, height, maxHeight, gap, inset, space, and translate core plugins. </h3>

<h3> Use the spacing key in the theme section of your tailwind.config.js file to customize Tailwind’s default spacing/sizing scale. </h3>

module.exports = {
  theme: {
    spacing: {
      '1': '8px',
      '2': '12px',
      '3': '16px',
      '4': '24px',
      '5': '32px',
      '6': '48px',
    }
  }
}

Extending the default spacing scale
As described in the theme documentation, if you’d like to extend the default spacing scale, you can do so using the theme.extend.spacing section of your tailwind.config.js file:

tailwind.config.js
module.exports = {
  theme: {
    extend: {
      spacing: {
        '13': '3.25rem',
        '15': '3.75rem',
        '128': '32rem',
        '144': '36rem',
      }
    }
  }
}
This will generate classes like p-13, m-15, and h-128 in addition to all of Tailwind’s default spacing/sizing utilities