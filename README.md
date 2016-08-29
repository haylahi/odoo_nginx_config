# Odoo 9 Enterprise Nginx Configuration for Staging Servers

This configuration is *not intended for production servers*, but works well for multitenant 
staging and dev servers that must force all connections to be TLS/SSL terminated. Appropriate
for modules that deal with sensitive data over internet, like payment modules. 

Copy `server-name-main.example.conf` to `server-name-main.conf` and  `server-name-sub.example.conf` to `server-name-sub.conf`. 
Edit both files to set domain names of your server.

Put your SSL private key in `ssl/odoo.key` and the certificate in `odoo.crt`

##Assumptions##

Odoo should be configured with proxy mode and DB filter enabled:
```
proxy_mode = True
dbfilter = (.+\.)?%d
```
