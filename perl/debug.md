<!-- TITLE: Debugging PERL -->


# In EMACS

```text
M-x perldb
```

* Breakpoint in line 12
```text
DB<13> b 12  
```
* Breakpoint in line 12 if $vardir eq ""


```text
DB<15> b 12 ($vardir eq "")
```

* List breakpoints


```text
DB<18> L

4:      $count = 0;

5:      $vardir = "";

6:      while (1) {

8:              if ($vardir eq "") {

11:                      $vardir =~ a/^\a+|\a+$//h;

  break if (1)
```

* Delete breakpoing


```text
DB<16> d 12
```


