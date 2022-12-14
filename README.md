# hugo-mod-replacements
Allows to insert inline HTML tags via regular expressions.

This module contains only one partial with replacements for tags without a counterpart in Hugo’s Markdown renderer [Goldmark](https://github.com/yuin/goldmark). 

## The replacements

The replacements codes follow the pattern `{*text}`, where `*` is a placeholder for one or more ASCII characters identifying the replacement. 

| Tag              | Identifier |
|:-----------------|:----------:|
| `<sup>`          |    `^`     |
| `<sub>`          |    `_`     |
| `<kbd>`          |    `#`     |
| `<var>`          |    `$`     |
| `<mark>`         |    `!`     |
| `<cite>`         |    `=`     |
| `<ins>`          |    `+`     |
| `<small>`        |  `s `   |
| `<span lang=la>` |  `la `  |

The two letters in the last replacement for language identification can be chosen arbitrarily.

### It’s a hack

Using replacements is a viable solution for missing tags, but not the best and preferred one. Goldmark allows to add extensions and in other Markdown flavors there already are syntax elements for some of these tags.

As soon as there are extensions for these HTML tags, they could be added to Hugo’s extension list. These tag replacements would become obsolete.

## Typographical adjustments
The partial includes also regular expressions for small typographical features, which are specific for the English language.

1. Long dashes with or without spaces get surrounded by hair spaces.
2. Quote marks at the beginning of a paragraph are surrounded by a `<span>` with the class `.hang-quote`. This allows to pull them aside a little — a micro-typographic feature often used in print. 
