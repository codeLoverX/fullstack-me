

1. You can optionally provide default font-feature-settings for each font in your project using a tuple of the form [fontFamilies, { fontFeatureSettings }] when configuring custom fonts.

2. Note that Tailwind does not automatically escape font names for you. If you’re using a font that contains an invalid identifier, wrap it in quotes or escape the invalid characters.


module.exports = {
  theme: {
    fontFamily: {
      'sans': [
        "Inter var, sans-serif",
        { fontFeatureSettings: '"cv11", "ss01"' },
      ],
      // Won't work:
      //  'sans': ['Exo 2', ...],
      // Add quotes:
      'sans': ['"Exo 2"', ...],
      // ...or escape the space:
      'sans': ['Exo\\ 2', ...],
      }
    }
}

Arbitrary values
If you need to use a one-off font-family value that doesn’t make sense to include in your theme, use square brackets to generate a property on the fly using any arbitrary value.

<p class="font-['Open_Sans']">
  <!-- ... -->
</p>