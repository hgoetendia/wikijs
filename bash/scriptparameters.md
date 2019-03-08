<!-- TITLE: Bash Script parameters -->

# Number of parameters entered
man bash
```text
Special Parameters
   #      Expands to the number of positional parameters in decimal.
```
Code

```sh
if [ "$#" -eq 0 ]; then
  echo "You did not pass any parameter budy"
fi
```

# Values of parameters entered


```text
`$1` for `value of 1st argument passed`
`$2` for 'value of 2nd argument passed`
```
