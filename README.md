# tree-sitter-djot (php-collective fork)

> Fork of [`treeman/tree-sitter-djot`](https://codeberg.org/treeman/tree-sitter-djot) maintained by [php-collective](https://github.com/php-collective).
>
> **Why this fork:** Zed's WASM runtime cannot resolve libc `isalnum` from the upstream scanner. This fork carries a one-line ASCII inline replacement so the grammar loads cleanly in Zed and other WASM-host Tree-sitter consumers. The patch is small and we expect to retire the fork once upstream lands an equivalent change.
>
> **Also planned for this fork:** djot-php-specific syntax additions (wikilinks `[[Page|label]]`, user mentions, abbreviation definitions `*[KEY]:`, fenced comment blocks `%%%`, captions `^ text`). These will be added as separate commits if upstream doesn't accept them.

---

This is an experimental [Tree-sitter][] grammar for [Djot][].

# Features

Aims to be fully feature complete with the [Djot specification][] with a few extra features:


- Parses an optional frontmatter at the very start of the file, e.g:

  ````
  ---toml
  tag = "Some value"
  ---
  ````

- Parses tight sublists.

  Normally in Djot you need to surround a list inside a list with spaces:

  ```
  - List

    - Another
    - list
  ```

  This grammar doesn't require a space and recognizes this as a sublist:

  ```
  - List
    - Another
    - list
   ```

- Parses standalone `TODO`, `NOTE` and `FIXME`.

[Tree-sitter]: https://tree-sitter.github.io/tree-sitter/
[Djot]: https://djot.net/
[Djot specification]: https://htmlpreview.github.io/?https://github.com/jgm/djot/blob/master/doc/syntax.html
