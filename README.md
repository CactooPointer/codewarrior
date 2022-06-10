# codewarrior

Codewarrior is just another tool for static code analysis. 
![Alt text](https://github.com/CoolerVoid/codewarrior/blob/master/doc/img/img1.png)
The tool uses HTTPd resources with TLS, design pattern follows the KISS principle.(https://en.wikipedia.org/wiki/KISS_principle)

# Video demo 
https://youtu.be/tZkllJ9mieU

# Features
* Code search by regex pattern
* Resources to custom rules
* HTTPd view with web socket resources
* Recursive scan 
* Syntax highlight by programming language

# Compile and run

You don't need to install it, but it must compile and run. 
Has full support for Linux and *BSD.

So, you needs to install OpenSSL-dev or OpenSSL-devel package
```
$ git clone https://github.com/CoolerVoid/codewarrior/; cd CodeWarrior
$ make
```
For example, if you need to create your cert and load...
```
$ cd cert; openssl req  -nodes -new -x509  -keyout key.pem -out cert.pem
$ cd ..
```
Note: use the name key.pem and cert.pem...because codewarrior use this file names to load resources.

Execute don't do "cd bin; ./warrior", follow example:
```
$ bin/warrior 
```

Open browser at *https://127.0.0.1:1345/index.html*   (dont write localhost use 127.0.0.1)

# Notes:
>* if screen stock, you can refresh the browser with F5 and try again.
>* If return error, port already in use... close it with this following:
``` 
$ fuser -k -n tcp 1345
```

* If you want to use the network, Whitelist to access server you can edit at "config/whitelist.conf". 
* Use chrome browser to run.
* Use 127.0.0.1 addr don't use localhost name.

# Tested at path:  
*https://github.com/joostvanveen/php-security-pitfalls*


# Tricks:
```
* if you want to change cert "cert/certpem.pem" generate with OpenSSL certificate and key and concatenate both...
* all HTML code and web sockets + javascript code you can view at path "web/".
* if you change the default port, you need to edit port in web/ at web sockets connection.
```

# Directories overview:
```
> web/ = local of javascripts and html and css sources
> src/ = C source code, this code talking with web socket 
> eggs/ = external modules to search codes using regex
> conf/whitelist.conf = list of IPs that have  access to the HTTPd server
> bin/ = file to execute...
> doc/ = at construction...
> lib/ = External libraries
> cert/ = loads your certificates for TLS here
``` 

# TODO:
* Add external Automatons for each language case
* Add load module with dlopen()
* Add ReDOS validator at regex calls
* Machine learning, so try use bag of Words with KNN

# Author: CoolerVoid
# Template by Pr0teus https://github.com/Pr0teus
# contact:coolerlair@gmail.com

# Point of attention
The purpose of this tool is to use in pentest, take attention if you have a proper authorization before to use that. I do not have responsibility for your actions. You can use a hammer to construct a house or destroy it, choose the law path, don't be a bad guy, remember.

