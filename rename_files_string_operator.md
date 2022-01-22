# Rename files in bash

Huanfa Chen

Updates: 2022/01/22

1. To replace all space in the file names with **underscore** for files of a given pattern

```bash
#!/bin/bash
for file in *.pdf *.doc; do mv "${file}" "${file// /_}"; done
```

Here the `${var//pattern/replacement}` operator is used.

You can replace ```*.pdf *.doc``` with any pattern.

e.g., **File name.pdf** becomes **File_name.pdf**

2. To keep the part of file name before the first occurrence of space in the file name:

e.g. **123 file name.pdf** becomes **123.pdf**

```bash
for file in *.pdf; do mv "${file}" "${file/\ */.pdf}"; done
```

Here the `${var//pattern/replacement}` operator is used. It means replacing **the first space and the following characters** with **.pdf**



# String operations

References: Section 34 in book ‘the Linux command line’

There is a large set of expansions that can be used to operate on strings. Many of these
expansions are particularly well suited for operations on pathnames.

## Removing parts of filenames

```
${parameter#pattern}
```

This expansion removes a leading portion of the *shortest matched string* contained in parameter defined
by pattern. pattern is a wildcard pattern like those used in pathname expansion. Test code:

```
foo=123 file.pdf.zip
echo ${foo#*.}
#pdf.zip
```

```
${parameter##pattern}
```

This expansion is similar to previous one, but it removes the longest matched string.

```
foo=123 file.pdf.zip
echo ${foo##*.}
#zip
```

## Replacing parts of filenames

```
${parameter/pattern/string}
${parameter//pattern/string}
${parameter/#pattern/string}
${parameter/%pattern/string}
```

This expansion performs a search-and-replace upon the contents of parameter. If text is
found matching wildcard pattern, it is replaced with the contents of string. In the normal
form, **only the first occurrence of pattern is replaced**. In the // form, **all occurrences are**
**replaced**. The /# form requires that **the match occur at the beginning of the string**, and
the /% form requires the match to occur at the end of the string. This can be used to alter the file types.

In every form, /string may be omitted, causing the text matched by pattern to be deleted.





