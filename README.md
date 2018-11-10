# Overview

Needle is a python3 script which performs sql injection. It currently supports
mysql, postgresql and mssql injection.

**Needle was created for educational purposes. Stay away from illegal activities.**

Needle assumes that you have python3 installed under /usr/bin/python3.
It also needs the requests,sys,time,re modules.

## Usage

```
path_to_script  [-h][-u url][-c cookies][-d distinguisher][-f save_file]
                [-user user][-p parameters][-s valid_search]
```

## Flags

-h: display help  
-u: the url to attempt sql injection to (write http://  or https://)  
-c: the session cookies  
-d: the distinguisher (look at README)  
-f: the file to save successful results  
-user: the username to login to the site  
-p: the parameters of the query  
-s: a valid search  

## Comments

* If you have to be logged in to perform a search then give the cookies to Needle
with the -c argument in the form: cookie1=something1/cookie2=something2 .
* If you want to save only the results regarding users give a valid username with
the -user argument, so Needle ditches all the tables that have no correlation
with users.
* You also have to provide a valid search with the -s argument. (eg cars, battery)
* In order to find the distinguisher you have to make a search, look at the source
code of the site and find a result. Then you have to find an occurrence that
information about that result is printed and provide that with the -d option.
The information about that result should be a string and not a number or boolean.
  * For example, say that a site returns the product name and the price for each
product and you make a search for product1. In the source code you see this:
\<br/>Product name: product1\<br/>Price: 100\<br/>. You can now provide the
distinguisher as lets say "Product name: DIST\<br/>" but NOT "Price: DIST\<br/>",
because 100 is a number. Use DIST at the place where different information is
printed for each product. Make sure you write something after DIST, like \<br/> in
the example. Do not use regular expressions or newlines.
  * Let's use the previous example and say that the url which we use for our
product1 search is http://example.com?product=product1&Submit=Submit#. The -u
argument will be http://example.com and the -q argument will be
product=product1/Submit=Submit, where & gets replaced with /. ? gets omitted and
also # at the end. If the method used by the site to make the search is post then
you have to use a proxy like Burp Suite or some other way to find out the
parameters and pass them in the -q argument like before.

Important: If sql injection fails and you have to login to the site to make a
search (meaning that you have to provide the session cookies to Needle) make sure
you are logged in to the site before starting Needle and you are passing the right
cookies to Needle.

### Contact Information

Konstantinos Sarantopoulos  
konsaranto@gmail.com
