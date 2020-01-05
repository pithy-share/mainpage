# mlog

## Introduction 
mlog is a lightweight c language log library .

![github](../img/github.png)
[source code in github](https://github.com/zyongzhangyong/mlog)

### File layout

* mlog.c
* mlog.h
* mlog_port.c
* mlog_port.h

## Usage 

### Port
Port `mlog_port.c`. Two functions need to port.

* `void get_time_str(char *time_buf)` return current time.
* `void print_by_user(char * str)` user print.

on Windows like this :
```c
#include <stdio.h>
#include <stdarg.h>

#include <windows.h>
void get_time_str(char *time_buf)
{
	SYSTEMTIME currentTime;
    GetSystemTime(&currentTime);
    sprintf(time_buf,"%04u.%02u.%02u %02u:%02u:%02u.%02u",           
     currentTime.wYear,currentTime.wMonth,currentTime.wDay,
     currentTime.wHour,currentTime.wMinute,currentTime.wSecond,
     currentTime.wMilliseconds);
}

void print_by_user(char * str) 
{
	printf("usrp %s\n", str);
}

```
### Use
example :
```c
#include "mlog.h"
#include "stdio.h"

int main(void)
{

	M_DEBUG("this is debug %s %d\n", "gggg", 123);
	
	M_INFO("this is info %s %d\n", "gggg", 123);

	M_WARN("this is warn %s %d\n", "gggg", 123);

	M_ERROR("this is error %s %d\n", "gggg", 123);

	M_FATAL("this is fatal %s %d\n", "gggg", 123);
	return 0;
}

```

## Configuration 
in `mlog.h`

name|info
-|-
MLOG_ENABLE|define this means enable log
MLOG_FILE_ENABLE|define this means enable output to file
MLOG_LEVEL_CUR|level of current 
LOG_STR_LEN|max len of one log string 
FILE_NAME_MAX_LEN| max len of filename
LOG_FILE_NAME|your file name
ONE_LOGFILE_MAX_LEN|max len of one log file  
MAX_FILE_CNTS|can output to multi files, this means how many output files 

