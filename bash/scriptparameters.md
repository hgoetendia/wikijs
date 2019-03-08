<!-- TITLE: Script parameters -->
<!-- SUBTITLE: A quick summary of Scriptparameters -->

# Number of parameters entered
man bash


```text
Special Parameters
   #      Expands to the number of positional parameters in decimal.
```


```sh
if [ "$#" -eq 0 ]; then
  echo "you did not pass any parameter"
fi
```
