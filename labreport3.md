# Lab Report 3 - Researching Commands

## Grep Command

[1] (Source: ChatGPT)
```bash
grep -r "search_string" directory/
```

The `-r` tag means search recursively, or search all files and folders within a directory including 
subfolders.

![grep1](screenshots/grep1.png)

Combining the `-r` tag with the `-l` tag that lists the files that contain the string:

![grep2](screenshots/grep2.png)

[2] (Source: ChatGPT, [linuxize.com](https://linuxize.com/post/regular-expressions-in-grep/))

```bash
grep -E "^[0-9]+$" file.txt
```

The `-E` tag means to search for a regular expression. A regular expression is a string with symbols 
that represent certain searching criteria. For example, the `^` (caret) symbol means match the string 
following the symbol if it is located at the start of a line.

