# The Inter Typeface (a npm distribution)

The CSS and web font files to easily self-host the [Inter font family](https://rsms.me/inter/) created by [Rasmus Andersson](https://rsms.me).

This repository is just a means of more easily distributing the font. It tracks the  releases of the main [Inter repository](https://github.com/rsms/inter) as best as I am able. Note that this repository only contains the `woff2` format but does generate and include latin-extended subsets for each font.

SCSS files are also available for use with the Sass preprocessor. The [`font-display` property](https://developer.mozilla.org/en-US/docs/Web/CSS/@font-face/font-display) can be overridden by setting `$inter-font-display` to a valid `font-display` value *before* importing the desired `.scss` file.

## Quick start

```sh
npm install --save inter-ui
```

### SCSS

Add the following to your SCSS to use the variable font with a non-variable fallback:

```scss
@use "~inter-ui/default" with (
  $inter-font-display: swap,
  $inter-font-path: '~inter-ui/web'
);

@use "~inter-ui/variable" with (
  $inter-font-display: swap,
  $inter-font-path: '~inter-ui/variable'
);

@include default.all;
@include variable.all;

html { font-family: "Inter", "system-ui"; }

@supports (font-variation-settings: normal) {
  html { font-family: "InterVariable", "system-ui"; }
}
```

Note that this `@use` syntax is [not currently supported in the node-sass or ruby sass implementations](https://sass-lang.com/documentation/at-rules/use). We recommend using the primary sass implementation: [dart sass](https://github.com/sass/dart-sass).

### JS/CSS

We have pre-built CSS files that you can include directly (with `font-display` being `swap`).

Add the following to your script:

```js
import "inter-ui/inter.css";
// Or use one of those versions:
// import "inter-ui/inter-latin.css"; // A subset of only English alphabet characters
// import "inter-ui/inter-display.css"; // The display font is optimised for XL text
// import "inter-ui/inter-display-latin.css";
// import "inter-ui/inter-variable.css";
// import "inter-ui/inter-variable-latin.css";
```

Add the following to your stylesheet:

```css
html { font-family: "Inter", "system-ui"; }

@supports (font-variation-settings: normal) {
  html { font-family: "InterVariable", "system-ui"; } /* If using the variable font */
}
```

## Modular imports

To avoid having to import all "font faces". You can also use only some of them via SCSS.

If you only want 400 and 700 you can specify exactly this.

```scss
@use "~inter-ui/default" as inter-ui with (
  $inter-font-path: "~inter-ui/web-latin"
);
@include inter-ui.weight-400;
@include inter-ui.weight-700;
```

## Versions

There are several versions you can choose from. To use them with the modules, just change the `$inter-font-path` to e.g. `Inter (web hinted)` or use the other pre-built CSS files.

### Hinted vs Unhinted

As detailed in the main repo:

> Inter font files comes in two versions:
>
> 1. "unhinted" -- Without TrueType hints (the default)
> 2. "hinted" -- With TrueType hints
>
> The TrueType hints are used by ClearType on Windows machines where ClearType is enabled. This usually changes the appearance of the fonts and can in some cases increase the legibility of text.
>
> Additionally, hints are little computer programs that takes up considerable disk space, meaning that font files with hints are larger than those without hints. This might be a consideration when using web fonts.

* SCSS use: set `$inter-font-path` to `Inter (web hinted)` or `Inter (web hinted latin)`
* JS/CSS use: import `inter-ui/inter-hinted.css` or `inter-ui/inter-hinted-latin.css`

### Latin

If you only need support for Latin characters, you can use this version. The normal `Inter (web)` version average filesize is between 150kb and 100kb, the reduced Latin version is on average 30kb per font.

This was generated using [glyphhanger](https://github.com/filamentgroup/glyphhanger). See `package.json` for the build script.

* SCSS use: set `$inter-font-path` to `Inter (web latin)` or `Inter (web hinted latin)`
* JS/CSS use: import `inter-ui/inter-latin.css` or `inter-ui/inter-hinted-latin.css`
