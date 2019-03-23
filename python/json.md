<!-- TITLE: Json -->

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

