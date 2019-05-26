<!-- TITLE: Yowsup Last Version -->

# Installing using virtual env


```sh
$ python -m venv yowsup-env
```
```sh
$ source yowsup-env/bin/activate
```

Requirements file


```sh
$ cat requirements.txt 
consonance==0.1.2
python-axolotl==0.2.2
protobuf>=3.6.0
six==1.10
```

Installing


```sh
$ pip install -r requirements.txt
$ pip install yowsup
```




# Enabling

## Activating


```sh
yowsup-cli registration --requestcode sms --phone 51XXXXXXXXX --cc 51 --mcc 716 --mnc 07 --env android
```

## Registering


```sh
yowsup-cli registration --register 391608 --phone 51XXXXXXXXX --cc 51 --env android
```

Output sample:


```text
I 2019-05-21 12:07:30,871 yowsup.common.http.warequest - b'{"status":"ok","login":"51XXXXXXXX","type":"new","edge_routing_info":"CAUIAg==","chat_dns_domain":"fb","security_code_set":false}\n'
{
    "__version__": 1,
    "cc": "51",
    "client_static_keypair": "XXXXXXXX==",
    "expid": "XXXX==",
    "fdid": "2XXXX",
    "id": "YXXXXX",
    "mcc": "716",
    "mnc": "07",
    "phone": "51XXXXX",
    "sim_mcc": "000",
    "sim_mnc": "000"
}
status: b'ok'
login: b'51XXXX'
type: b'new'
edge_routing_info: b'CXX=='
```

if you want save the json output in a file

## Testing demo


```sh
yowsup-cli demos  -c ./config.json --yowsup
```



