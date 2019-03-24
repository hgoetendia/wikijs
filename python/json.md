<!-- TITLE: Json -->


JSON syntax is not Python syntax. JSON requires double quotes for its strings.

Python dicts:

`{'Protl': {'dateTimeSent': '2019-03-24 14:17:33.743606', 'tenlId': 1, 'hostId': 1, 'boxId': 1, 'commun': {'commId': 1, 'sessid': 1, 'deviceId': 0, 'timeToLive': 30000}}}
`

JSON representation:

`{"Protl": {"dateTimeSent": "2019-03-24 14:17:33.743606", "tenlId": 1, "hostId": 1, "boxId": 1, "commun": {"commId": 1, "sessid": 1, "deviceId": 0, "timeToLive": 30000}}}
`

To change use this:


```python
import json

# mixing single and double quotes
data = {'jsonKey': 'jsonValue',"title": "hello world"}

# get string with all double quotes
json_string = json.dumps(data) 
```

# Read JSON configfile

Create a test json file 

test.json

```json
{
  "mydata1" : 1024,
  "mydata2" : 768
}
```

Reading


```python
import json

with open('test.json') as config_file:
    data = json.load(config_file)

data1 = data['mydata1']
data2 = data['mydata2']
print(data1)
print(data2)
```

