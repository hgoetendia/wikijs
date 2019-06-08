<!-- TITLE: Errno -->
<!-- SUBTITLE: A quick summary of Errno -->


```c_cpp

#include <stdio.h>
#include <string.h>
#include <errno.h>

int main ()
{
    FILE * pFile;
    pFile = fopen ("foounexist.file","r");
    if (pFile == NULL)
        printf ("Error opening file: %s\n",strerror(errno));
    return 0;
}
```
