# andesine: Readable and colourblind-friendly HTML output for R Markdown

# [See an example document here](https://rawcdn.githack.com/DesiQuintans/andesine/f168f30b0e4fd2126cad6b07f5557c195bbd3f26/example.html)

## Features

I (Desi) made this template to fit with as MS Word stylesheet I've been using for a while, and which is sort of becoming my personal brand. Besides that, it also deals with some shortcomings of the built-in themes and highlighters that have gotten me confused in the past.

1. Body text rendered in [Atkinson Hyperlegible](https://brailleinstitute.org/freefont) for easy reading.
2. Code rendered in [Fira Code](https://github.com/tonsky/FiraCode), with option to disable the ligatures.
3. Two syntax highlighting themes provided, one **colourblind-friendly** based on my [Pebble-safe RStudio editor theme](https://github.com/DesiQuintans/Pebble-safe/), and one *not** colourblind-friendly that is modified from Pandoc's *breezedark* highlighter. This readme is outputting with the Pebble-safe highlighter.
4. Dark code blocks and light output blocks make it instantly obvious which is which.
5. Visually prominent headings with more whitespace help when skimming through the document.
6. Basic sanities set up in the template ('last compiled' time, `sessioninfo()` dump, automated installation of my package manager [`librarian`](https://github.com/DesiQuintans/librarian)).


# Installation

Install `andesine` from GitHub:

```r
install.packages("remotes")
remotes::install_github("DesiQuintans/andesine")
```


# Usage

To make a new document, go to `File` → `New File` → `R Markdown...` → `From Template` → `Andesine (HTML)`.

This template does not use the 'theme' or 'css' YAML fields. Instead, 
it uses the `breezedark` highlighter to add style tags to the output 
HTML, and then the document is styled and highlighted by CSS that is 
embedded at the very end of the template (use code folding to see the
CSS chunks' names more clearly). 

Yes, the CSS is embedded, and not in external files. I did it this 
way so that the template itself was a single file, otherwise each new 
andesine document would have to be created in its own folder to 
accommodate the external files.


## Turning off Fira Code's programming ligatures

Fira Code (the monospace font for this template) includes programming ligatures, like turning the left-assign arrow `< -` into `←`. You might want to turn this off, *especially* if you're producing documents that will be reading by folks who are trying to learn R.

To turn ligatures off, search the template for `css no_ligatures`, and set that chunk to `eval=TRUE` (it is `FALSE` by default).


## Choosing a syntax highlighter

There are two syntax highlighting options included as CSS chunks at the end of the template:

1. `highlight_andesine_dark`, not colourblind-friendly. Modified from `breezedark` to make the function names easier to see against the dark background.
2. **(Default)** `highlight_pebblesafe_dark`, colourblind-friendly. Based on my [Pebble-safe RStudio editor theme](https://github.com/DesiQuintans/Pebble-safe/).

The last highlighting CSS chunk to appear in the document is what gets used.
