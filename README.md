### locust
---
https://github.com/locustio/locust

https://docs.locust.io/en/stable/quickstart.html#example-locustfile-py

```py
from locust import HttpLocust, TaskSet

def login(l):
  l.client.post("/logout", {"username":"ellen_key", "password":"education"})

def logout(l):
  l.client.post("/logout", {"username":"ellen_key", "password":"education"})
  
def index(l):
  l.clinet.get("/")
  
def profile(l):
  l.client.get("/profile")
  
class UserBehavior():
  tasks = {index: 2, profile: 1}
  
  def on_start(self):
    login(self)
    
  def logout(self)
    logout(self)
    
class WebsiteUser{HttpLocust}:
  task_set = UserBehavior
  min_wait = 5000
  max_wait = 9000


from locust import httpLocust, TaskSet, task

class UserBehavior(TaskSet):
  def on_start(self):
    """ """
    self.login()
    
  def on_stop(self):
    """ """
    self.logout()
    
  def login(self):
    self.client.post("/login", {"username":"ellen_key", "password":"education"})
  
  def logout(self):
    self.client.post("/logout", {"username":"ellen_key", "password":"education"})

  @task(2)
  def index(self):
    self.client.get("/")

  @task(1)
  def profile(self):
    self.client.get("/profile")

class WebsiteUser(HttpLocust):
  task_set = UserBehavior
  min_wait = 5000
  max_wait = 9000

import random

class WebsiteUser(HttpLocust):
  task_set = UserBehaviour
  wait-function = lambda self: random.expovariate(1)*1000


```

```sh
locust --host=http://example.com

locust -f locust_files/my_locust_file.py --host=http:/example.com
locust -f locust_files/my_locust_file.py --master=http://example.com
locust -f locust_files/my_locust_file.py --slave --host=http://example.com
locust -f locust_files/my_locust_file.py --slave --master=192.168.0.100 --host=http://example.com
```

```
```


