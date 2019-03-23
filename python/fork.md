<!-- TITLE: Fork -->
<!-- SUBTITLE: A quick summary of Fork -->

# Fork

```python
import os

newpid = os.fork()

if newpid == 0:
   #Child
   pass 
else:
   #Father
   pids = (os.getpid(), newpid)
   print("parent: %d, child: %d\n" % pids)
```

   