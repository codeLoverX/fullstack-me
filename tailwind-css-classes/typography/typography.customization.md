

1. You can optionally provide default font-feature-settings for each font in your project using a tuple of the form [fontFamilies, { fontFeatureSettings }] when configuring custom fonts.

2. Note that Tailwind does not automatically escape font names for you. If you’re using a font that contains an invalid identifier, wrap it in quotes or escape the invalid characters.


module.exports = {
  theme: {
    >>> classname: font-sans, font-mono, font-serif
    >>> css property: font-family
    >>> arbitrary: font-["Inter"]
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
    },
    >>> classname: text-sm, text-xl, text-5xl
    >>> css property: font-size
    >>> arbitrary: text-[14px]
    fontSize: {
      sm: '0.8rem',
      xl: '1.25rem',
      '4xl': '2.441rem',
      '5xl': '3.052rem',
    },
    >>> classname: font-hairline, font-extra-light, font-light
    >>> css property: font-weight
    >>> arbitrary: font-[1100]
    fontWeight: {
      hairline: 100,
      'extra-light': 100,
      thin: 200,
      light: 300,
      normal: 400,
      medium: 500
    },
    >>> classname: tracking-tight, tracking-tighter
    >>> css property: letter-spacing
    >>> arbitrary: tracking-[.25em]
    letterSpacing: {
      tightest: '-.075em',
      tighter: '-.05em',
      tight: '-.025em',
    },
    >>> classname: leading-loose
    >>> css property: line-height
    >>> arbitrary: leading-[.25em]
     lineHeight: {
        'extra-loose': '2.5',
        '12': '3rem',
      }
}

Arbitrary values
If you need to use a one-off font-family value that doesn’t make sense to include in your theme, use square brackets to generate a property on the fly using any arbitrary value.

<p class="font-['Open_Sans']">
  <!-- ... -->
</p>