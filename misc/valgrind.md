<!-- TITLE: Valgrind -->
<!-- SUBTITLE: A quick summary of Valgrind -->


# Check memory leakings

```sh
$ valgrind --leak-check=full --show-leak-kinds=all --track-origins=yes --verbose --log-file=valgrind-out.txt ./executable exampleParam1
```
