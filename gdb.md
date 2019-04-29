<!-- TITLE: Gdb -->
<!-- SUBTITLE: A quick summary of Gdb -->


# Breakpoints

## Breakpoint in main file

In line 91:

```text
(gdb) b 91

```

or

```text
(gdb) break 91

```

## Breakpoint in certain file

```text
(gdb) b business.c:91

```

# Pretty print structures

```json
(gdb) set print pretty on

(gdb) p test
$4 = {
  username = "ClienteA", '\000' <repeats 31 times>, 
  detail = {    
    cuanto = "1\000\000\000\000\000\000\000\000", 
    mensae = "Hola, esto es un mensaje de prueba", '\000' <repeats 1965 times>, 
    tid = "T3915uqisdsr", '\000' <repeats 20 times>
  },   
  date = "2019-03-11 15:09:39", '\000' <repeats 20 times>
}
(gdb) 
```
