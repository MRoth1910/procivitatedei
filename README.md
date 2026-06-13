# procivitatedei

# about
Booklets for the Pro Civitate Dei conference which features the Holy Mass and Divine Office daily in the traditional Latin rite.

# License
License shared with the Nocturnale Romanum project license as some of the code originated from there. So this license (or maybe a compatible one) must be used as well.

# Fonts

You can use the `ebgaramond` package in TeXLive, but I simply use the local font installation that I have had forever (fonts are available in the repo: fair warning, there are some problems (kerning is also not meant to take place between roman and italic type in the same word, thus I use LaTeX to fix this.

However, most of them can be solved with `fontspec` or being creative.

Why ligatures (including -st and -ct)? Simply because I find them beautiful, and although certain Latinists are more Augustan/republican in their Latin, there is a long pedigree of dividing words including in ecclesiastical Latin like this (admittedly, I have to watch to see if some words split awkwardly leaving a vowel widowed on a line, but look at the _Liber Usualis:_ that's how Solesmes syllabified words! Although Solesmes and Desclée later abandoned a heavy use of ligatures, you find them in the earliest versions of the gradual and the _Liber Responsorialis_ of Dom Pothier. These are all done quite easily with the OpenType format used by the creator(s) of EB Garamond and therefore with `fontspec`.

# TeX ins and outs

main.tex type files beging with ```% !TEX TS-program = lualatexmk
% !TEX parameter =  --shell-escape```

The first "magic comment" is the way, in TeXShop with TeXLive (via MacTeX) on macOS to use LuaLaTeX (required for GregorioTeX and recommended for all compilations, as it is the most up-to-date form of LaTeX for which all modern packages are configured) and to automatically typeset again or a third time etc. as needed, necessary in versions of Gregorio prior to 6.2 (I am running 6.1 as of June 2026) for typesestting the line breaks and therefore the staff distances correctly (before any tweaking is necessary: see  `gregorioref.pdf` for more details), for typesetting features such as the braces needed in mode 3 psalmody, and necesary for other features such as cross-references (including a table of contents, works with indices, etc.) if one chooses to include them, as we have here with page references and a TOC.

The second magic comment is required to use GregorioTeX as an external program.

I recommend finding out how to use magic comments in your editor if you use one (you need to specify `LuaLaTeX + se` and `latexmk` when typesetting at the command line per your system's instructions)

But the specific way to type the magic comment (sometimes case-senstive) and which ones are accepted depend on your editor. I don't recommend trying to use `shell-escape` all the time; that's unnecessary and introduces a security risk. I don't recommend changing the default `pdflatex` (even though it's outdated) unless you are a true expert: setting this in your documents lets LaTeX do everything for you, without an error message for something that keeps your document from compiling.

## other

The booklet size for PCD is A4, the standard European (ISO) paper size. However, with `geometry`, one can even make custom, not-available sizes or use any other standard (see that package's documentation). Then one just needs to tweak the dimensions, but I have used these settings with American letter paper, smaller paper, etc. with very few changes.

# How did I make the title?

See the `pcd.tex` file and change the words and paper size. Then in Inkscape, you need to :

1. Import the PDF: Open Inkscape, click File > Open, and select your PDF. In the PDF import settings window, make sure to set the Text import option to "Embed fonts" or "Import text as text" (depending on your Inkscape version) so the text is recognized.
2. (I probably skipped this step: start over if you have problems and include it if you find the result unsatisfactory): Ungroup Elements: By default, the PDF imports as a single group. Select the document (or press Ctrl + A) and press Ctrl + Shift + G to ungroup elements. You may need to press this a few times to fully separate the text blocks.
3. Convert to Paths (Optional - required if you are using a cutting machine): If you want to convert the text to vector outlines so it stays perfectly shaped across all devices:Select your text using the Select Tool (F1).Go to the top menu and click Path > Object to Path.Note: This turns your letters into vector nodes so you can edit their shapes, but the text will no longer be editable as regular typed words.
4. Save as SVG: Go to File > Save As and choose Plain SVG (*.svg) from the dropdown: this apparently is required to use the `svg` package.

If you don't have Inkscape or don't wish to run it multiple times: just use `\includegraphics` (the command works with `graphicx` included in the preamble file named `commonheaders_pcd_2026.tex`) to insert a PNG version.
