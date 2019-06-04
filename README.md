# peak-base.css

Base style fo the Peak Besign System - includes only basic elemental styling and themes, no layout or structure patterns

**Usage**

A `theme` file is required to be `@import`-ed prior to `peak-base.css`. The theme file will pre-load all required vaiables for the Peak base styling:

example:

```
@import '~@wealthbar/peak-base.css/theme/wealthbar.scss';
@import '~@wealthbar/peak-base.css';
```

Additionally, `theme` files can be loaded on a per component/page basis to allow use of colour and setting variables within the templated file. Ideally this should be handled by webpack so the developers aren't bothered with having to import a theme everytime they choose to use a variable in the template. The biggest advantage of the webpack setup is the ability to switch theme based on build config ENV variables.

example webpack setup:

```
const theme = JSON.parse(configEnv.WHITELABEL_BRAND);

…

loader: 'sass-loader',
  options: {
    data: `@import "~@wealthbar/peak-base.css/theme/${theme}.scss";`,
    includePaths: ['src/styles'],
  },
```
Another
