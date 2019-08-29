# peak-style

This package is used to install the SCSS or CSS style for the *Peak Design System*. Included in this package:
* *Themes* - The colour values variables and settings associated with the brand (SCSS only for now).
* *Base styles* - Basic HTML document setup, typography and elemental styling. No layout or structure patterns.
* *Pattern library* - a resource of commonly used patterns for component structures and page layout.

## Usage

### Option 1 - SCSS
A `theme` file is required to be `@import`-ed prior to the other style files. The theme file will pre-load all required vaiables for the for `base` styling and the `patterns` library. `base` styles are also required prior to the `pattern` files. These steps ensures the cascade of styles works as intended.

**example:**

```
@import '~@wealthbar/peak-style/scss/theme/wealthbar';
@import '~@wealthbar/peak-style/scss/base/index';
@import '~@wealthbar/peak-style/scss/patterns/index';
```
*OR* to load both `base` and `patterns` in one shot:

```
@import '~@wealthbar/peak-style/scss/theme/wealthbar';
@import '~@wealthbar/peak-style/scss/index';
```

Additionally, `theme` files can be loaded on a per component/page basis to allow use of colour and setting variables within the templated file. Ideally this should be handled by webpack so the developers aren't bothered with having to import a theme everytime they choose to use a variable in the template. The biggest advantage of the webpack setup is the ability to switch theme based on build config ENV variables.

**example webpack setup:**

```
const theme = JSON.parse(configEnv.WHITELABEL_BRAND);

…

loader: 'sass-loader',
  options: {
    data: `@import "~@wealthbar/peak-style/theme/${theme}.scss";`,
    includePaths: ['src/styles'],
  },
```
### Option 2 - CSS

CSS files are compiled based on `theme` and style package, they are directly imported into any html file. `base` and `patterns` for each theme are split into different files to save weight. As a result of the pre-compile there is *no access* to SCSS variables outside the scope of the file.

`theme-base` - minimal css  (reset, basic elements, typography, minimal button and input styling)
`theme-patterns` - common css patterns applied via classes (button and input style options)

So if you want the *wealthbar* themed *base* styles it is served as `wealthbar-base.css`

**example:**
```
<head>
  <link rel="stylesheet" type="text/css" href="wealthbar-base.css" media="screen" />
  <link rel="stylesheet" type="text/css" href="wealthbar-patterns.css" media="screen" />
</head>
```
