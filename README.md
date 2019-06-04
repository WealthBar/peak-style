# peak-base.css

Base style fo the Peak Besign System - includes only basic elemental styling and themes, no layout or structure patterns

**Usage**

A `theme` file is required to be `@import`-ed prior to the `index.scss` file the theme file will pre-load all required vaiables for the Peak base styling:

eg:

```
@import '~@wealthbar/peak-base.css/theme/wealthbar.scss';
@import '~@wealthbar/peak-base.css/index';
```

`theme` files can be loaded on a per app/component/page basis to allow use of colour and setting variables within the templated file. Ideally this can be handled by webpack to that it is auto-magically loaded without the developer needing to worry about import.

eg webpack setup:

```
loader: 'sass-loader',
  options: {
    data: `@import "~@wealthbar/peak-base.css/theme/${theme}.scss";`,
    includePaths: ['src/styles'],
  },
```
