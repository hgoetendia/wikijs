<!-- TITLE: Replace characters to others -->


# Replace pipe to coma ( | to , )


```sh
sed 's/|/,/g' filewithpipes.txt  > filewithcomas.csv
```

# Replace tab with coma ( TAB to CSV )
```sh
$ cat data.tsv | tr "\\t" "," > data.csv
```