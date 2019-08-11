<!-- TITLE: Sizeof -->

# sizeof single struct member in C

```c_cpp
typedef struct { 
     char class[40];
 } ub_minfo_cmd_t;

printf("%d\n", sizeof(((ub_minfo_cmd_t *)0)->class));
```


Output


```text
40
```
