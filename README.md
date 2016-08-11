# Odoo 9 Enterprise Nginx Configuration for Staging Servers

This configuration is *not intended for production servers*, but works well for multitenant 
staging and dev servers that must force all connections to be TLS/SSL terminated. Appropriate
for modules that deal with sensitive data over internet, like payment modules. 

Copy `base-name.example.conf` to `base-name.conf`. Edit it to set the domain name of your 
server. The configuration will allow you to access that domain name and all subdomains below it.

Put your SSL private key in `ssl/odoo.key` and the certificate in `odoo.crt`

##Assumptions##

Odoo should be configured with proxy mode and DB filter enabled:
```
proxy_mode = True
dbfilter = (.+\.)?%d
```
