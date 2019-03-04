# Overview

Needle is a python3 script which performs sql injection. It currently supports
mysql, postgresql and mssql injection.

**Needle was created for educational purposes. Stay away from illegal activities.**

Needle assumes that you have python3 installed under /usr/bin/python3.
It also needs the requests,sys,time,re modules.

## Usage

```
path_to_script [-h][-u url][-c cookies][-f save_file]
```

## Flags

-h: display help  
-u: the url to attempt sql injection to (http(s)://url?parameter1=value1&...)  
-c: the session cookies  
-f: the file to save successful results  

## Comments

* If you have to be logged in to perform a search then give the cookies to Needle
with the -c argument in the form: cookie1=something1/cookie2=something2...

Important: If you have to login to the site to make a search (meaning that you have to provide the session cookies to Needle)
make sure you are logged in to the site before starting Needle and you are passing the right cookies to Needle.

### Contact Information

Konstantinos Sarantopoulos  
konsaranto@protonmail.com
