# aritester
Web app to test Asterisk ARI (asterisk REST api)

## Description
ARI tester is a basic web app userful to test asterisk REST api.

## Install
Assuming an installation standard of asterisk, you need to put the file 
aritester.html in the directory:
```
  /var/lib/asterisk/static-http/
```  
then edit the file /etc/asterisk/http.conf to have:
```
[general]
enabled = yes
enablestatic = yes
bindaddr = 0.0.0.0
allowed_origins = *
```
and the file /etc/asterisk/ari.conf to have:
```
[general]
enabled = yes
pretty = yes

[asterisk]
type = user
read_only = no
password = asterisk
```
(obviously changing users and password )

in the dialplan (file /etc/asterisk/extensions.conf) you should have
a stasis extension:
```
exten => 6100,1,NoOp()
 same =>      n,Stasis(attendant)
 same =>      n,Hangup()
```

## Run
Start asterisk and open a browser to the address:
```
http://<ipaddress>:8088/static/aritester.html
```
then put username, password and stasis application in the form and
click login.

## Author
Author: Daniele Pallastrelli

Twitter: @DPallastrelli

## License
ARI tester is released under the [MIT license][MIT].

[MIT]:LICENSE
