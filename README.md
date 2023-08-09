# hugo-mod-replacements
Allows to insert inline HTML tags via regular expressions.

This module contains only one partial with replacements for tags without a counterpart in Hugo’s Markdown renderer [Goldmark](https://github.com/yuin/goldmark). 

## The replacements

The replacements codes follow the pattern `{?text}`, where `?` is a placeholder for one or more ASCII characters identifying the replacement. 

| Tag              | Identifier |
|:-----------------|:----------:|
| `<sup>`          |    `^`     |
| `<sub>`          |    `_`     |
| `<kbd>`          |    `~`     |
| `<var>`          |    `$`     |
| `<mark>`         |    `!`     |
| `<cite>`         |    `=`     |
| `<ins>`          |    `+`     |
| `<br class="br-cond"> `|    `/`     |
| `<small>`        |    `s `    |
| `<span lang="la">` |   `la `    |

- The break replacement is meant for conditional breaks in headings and titles and needs to be handled explicitly by its CSS class. Don’t use it without styling --- Markdown already has a line-break.

- The last two regular expressions with alphabetic character identifiers are expecting a space character before the content of the tag.

- The two letters for the `<span lang=la>` can be chosen arbitrarily. This replacement is not meant for complete Markdown blocks. A Markdown attribute like `{lang="la"}` can accomplish this already.

### It’s mostly a hack

Using replacements is a working solution for missing tags, but not always the best and preferred one. Goldmark allows adding extensions. Other Markdown flavors already offer syntax elements for some of these tags.

As soon as there are extensions for these HTML tags, they could be added to Hugo’s extension list. These tag replacements would become obsolete.

## Typographical adjustments
The partial includes also regular expressions for small typographical features, which are specific for the English language.

1. Long dashes with or without spaces get surrounded by hair spaces.
2. Quote marks at the beginning of a paragraph are surrounded by a `<span>` with the class `.hang-quote`. This allows to pull them aside a little — a micro-typographic feature often used in print. 
