<!-- TITLE: Split -->
<!-- SUBTITLE: A quick summary of Split -->

# Split a file into equal parts, without breaking individual lines

l = Leter L

```sh
split -n l/5 your_file.txt

```

no need for scripting here.

From the man file, CHUNKS  may  be:

l/N     split into N files without splitting lines

Or use (split every 75 lines)

```sh
split --lines=75 your_file.txt
```
