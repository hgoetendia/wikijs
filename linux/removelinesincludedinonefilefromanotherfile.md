<!-- TITLE: Remove lines included in one file from another file -->


```sh
grep -Fvx -f partial.list complete.list >remaining.list
```
