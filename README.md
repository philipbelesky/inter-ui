# Typeface-Inter

The CSS and web font files to easily self-host the [Inter font family](https://rsms.me/inter/) created by [Rasmus Andersson](https://rsms.me).

This repository is just a means of more easily distributing the font. It tracks the  releases of the main [inter repository](https://github.com/rsms/inter) as best as I am able.

At present it only contains the `woff` and `woff2` formats. As a result it supports versions of Chrome 5; Safari 5.1; Firefox 3.6; Opera 11.5; IE 9; Android 4.4; iOS 5.1 and above.

SCSS files are also available for use with the Sass preprocessor. The [`font-display` property](https://developer.mozilla.org/en-US/docs/Web/CSS/@font-face/font-display) can be overridden by setting `$inter-font-display` to a valid `font-display` value *before* importing the desired `.scss` file.

## Modular imports

To avoid having to import all "font faces". You can also use only some of them via SCSS.

If you only want 400 and 700 you can specify exactly this.
```scss
@use "~inter-ui/default" as inter-ui with (
	$inter-font-path: "~inter-ui/Inter (web)"
);
@include inter-ui.weight-400;
@include inter-ui.weight-700;
```

## Hinted vs Unhinted

As detailed in the main repo:

> Inter font files comes in two versions:
>
> 1. "unhinted" -- Without TrueType hints (the default)
> 2. "hinted" -- With TrueType hints
>
> The TrueType hints are used by ClearType on Windows machines where ClearType
is enabled. This usually changes the appearance of the fonts and can in some
cases increase the legibility of text.
>
> Additionally, hints are little computer programs that takes up considerable
disk space, meaning that font files with hints are larger than those without
hints. This might be a consideration when using web fonts.
