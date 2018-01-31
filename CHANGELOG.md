Changelog
=========


4.0.1 & 4.0.2 - 01/31/18
------------------------

- `local()` always comes first in `@font-face` `src` order.
- Fix typos in docs


4.0.0 - 01/30/18
----------------
*Compared against 3.1.0 -
for incremental changes,
see the 3.2 beta changelogs…*

- BREAKING: Change `$font-path` default to `''` (empty string)
  so that no path is prepended to fonts without explicit settings.
- BREAKING: Remove `$font-formats` global,
  in favor of `formats` key inside font-maps.
  - `font-face()` mixin no longer has `$formats` parameter.
  - `import-webfonts()` mixin no longer has `$formats` parameter.
- BREAKING: We no longer accept `regular` as a font-variant.
  Use the CSS-friendly `normal` instead.
- BREAKING/NEW: We now sort font-face src into the proper order for importing,
  based on the [fontsquirrel generated syntax][fs].
- BUGFIX: `font-family` function/mixin return proper font-name
  when given an alias keys.
- NEW: Allow sub-maps for each font variant (in addition to strings),
  optionally containing any or all of the following keys:
  - `path`: generic path to font-files for the given variant,
    the same as providing a string instead of a map.
  - `svgid` {string}: the proper fragment ID for svg fonts, as needed.
  - `local` {list}: list of font-names to include as `local()` src
    for the given variant.
  - `<format>` {string}: optionally provide different paths per font-format,
    Base64 font data, or additional formats for importing.
- NEW: Allow either string or number values
  for font-weights (e.g. `200` or `'200'` ).
- New: Supports `unicode-range` CSS property in font maps,
  as [described on MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/@font-face/unicode-range).

[fs]: https://www.fontsquirrel.com/tools/webfont-generator


3.2.0-beta.2 - 01/23/18
-----------------------
- BREAKING: Move `svgid` and `local` into font-variant sub-maps,
  since the required names are variant-specific.
- BREAKING: Remove `$font-formats` global,
  in favor of `formats` key inside font-maps.
  - `font-face()` mixin no longer has `$formats` parameter.
  - `import-webfonts()` mixin no longer has `$formats` parameter.
- BREAKING: Change `$font-path` default to `''` (empty string)
  so that no path is prepended to fonts without explicit settings.
- BUGFIX: `font-family` function/mixin return proper font-name
  when given alias keys.
- INTERNAL: Re-structure internal logic to normalize font maps,
  and handle additional font options.


3.2.0-beta.1 - 11/20/17
-----------------------
- NEW: Add `svgid` (string) option to font maps,
  for defining an id suffix in `svg` font urls.
- NEW: Add `local` (list) option to font maps,
  and allow `'local'` font-format value,
  to output any number of given `local("font-name")` src values.
  If the local key is undefined, we fall back to the font name.
- NEW: Allow either string or number values
  for font-weights (e.g. `200` or `'200'` ).
- NEW: Allow font-variants to define a sub-map
  of format/path pairs rather than a single relative path -
  especially useful for defining data-uri embedded fonts.
- NEW: Format data-uri `src` values correctly.


3.1.0 - 09/28/17
----------------

- NEW: `add-font` mixin makes font-config organization simpler


3.0.1 - 09/13/17
----------------

- Update docs.


3.0.0 - 09/12/17
----------------

- BREAKING: Use proper `::` syntax for pseudo-elements
- BREAKING: Set `pointer-events: none` on hidden text


2.1.0 — 12/09/16
----------------

- Document `$font` properties
- Add `false` option for font-variants,
  to allow documentation without triggering imports
- Test remaining mixins:
  `font-face`, `import-webfonts`, and `_import-font-face`


2.0.0 - 02/22/16
----------------

- NEW: `is-hidden()` mixin for screen-reader accessible, hidden text
- NEW: Add pseudo-element helper mixins:
  `before()`, `after()`, and `wrap-content()`
- BUGFIX: Add quotes to font url
- BREAKING: re-write font-helpers
