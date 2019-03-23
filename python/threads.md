<!-- TITLE: Threads -->
<!-- SUBTITLE: A quick summary of Threads -->

# Simple

```python

import threading
import time

def loop1_10():
    for i in range(1, 11):
        time.sleep(1)
        print(i)

t = threading.Thread(target=loop1_10)
t.start()
```

# Simple with object

```python
#!/usr/bin/env python

import threading
import time


class MyThread(threading.Thread):
    def run(self):
        print("{} started!".format(self.getName()))              # "Thread-x started!"
        time.sleep(1)                                      # Pretend to work for a second
        print("{} finished!".format(self.getName()))             # "Thread-x finished!"
def main():
    for x in range(4):                                     # Four times...
        mythread = MyThread(name = "Thread-{}".format(x + 1))  # ...Instantiate a thread and pass a unique ID to it
        mythread.start()                                   # ...Start the thread, invoke the run method
        time.sleep(.9)                                     # ...Wait 0.9 seconds before starting another
if __name__ == '__main__':main()
```

# Wait to stop

## Blocking way
```python

import threading
import time

def loop1_10():
    for i in range(1, 11):
        time.sleep(1)
        print(i)

t = threading.Thread(target=loop1_10)
t.start()
t.join()
```

## No blocking way

```python

import threading
import time

def loop1_10():
    for i in range(1, 11):
        time.sleep(1)
        print(i)

t = threading.Thread(target=loop1_10)
t.start()
t.join(timeout=5.0)#wait 5 seconds
```

# Arguments to thread

```python
#!/usr/bin/python

import threading, time

def countTo(x,delay):
    print(x)
		print(delay)

t = threading.Thread(target=countTo,args=(4,0.25))

t.start()
```
