# Simple-abbreviations Extension for Quarto

This extension allows user defined simple text replacement macros in the yaml of a quarto document:
in the documents yaml, add your abbreviations as keys starting with `+`, e.g. 
```
---
+myformula: the probably most well known formula $a^2+b^2=\mathrm{youknow}$ 
+myqurl: https://quarto.org/docs/extensions/filters.html
---
This will be an article about +myformula^[+myformula is famous]

Please read more about creating filters in [Quarto's documentation](+myqurl)]

```
Then all occurences of the same key (starting with +) in the document are replaced by the value.

UI syntax follows [Scott Koga-Browes](https://github.com/scokobro)' beautiful python-based pandoc filter [pandoc-abbreviations](https://github.com/scokobro/pandoc-abbreviations).

## Installing

```bash
quarto add ute/simple-abbreviations
```

This will install the extension under the `_extensions` subdirectory.
If you're using version control, you will want to check in this directory.

## Using

For each abbreviation, add one line to the yaml. The keys have to start with a `+`, also when using the abbreviation later in the text. 

Leading and trailing blanks get trimmed. You can concatenate abbreviations.

Abbreviations can also be used to specify text and targets in links.

Keys should not be contained in each other, specifying keys `+do` and `+doo` in the same would be ambiguous.

Abbreviation texts may be enquoted to avoid problems with yaml syntax, e.g. when they start with `- `.

Keys
```
+do: "- doodledoo -"
+dab: '"- dab - "'
+daa: daaah
```
translate `+do+dab+daa` to `- doodledoo -"- dab -"daaah` 





## Example

Here is the source code for a minimal example: [example.qmd](example.qmd).

