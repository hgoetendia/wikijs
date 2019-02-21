<!-- TITLE: Iptables -->

# Show rules

## List Rules by Specification

To list out all of the active iptables rules by specification, run the iptables command with the -S option:


```sh
sudo iptables -S
```

## List specific chain
```sh
sudo iptables -S TCP
```
## List tules as tables
```sh
sudo iptables -L
```
```sh
sudo iptables -L INPUT
```