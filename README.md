# Odoo 9 Enterprise Nginx Configuration for Staging Servers

This configuration is *not intended for production servers*, but works well for multitenant 
staging and dev servers that must force all connections to be TLS/SSL terminated. Appropriate
for modules that deal with sensitive data over internet, like payment modules. 

Copy `server-name-main.example.conf` to `server-name-main.conf` and  `server-name-sub.example.conf` to `server-name-sub.conf`. 
Edit both files to set domain names of your server.

Put your SSL private key in `ssl/odoo.key` and the certificate in `ssl/odoo.crt`

## Assumptions

Odoo should be configured with proxy mode and DB filter enabled:
```
proxy_mode = True
dbfilter = (.+\.)?%d
```

## Longpolling and dev_mode
In multiprocess mode odoo runs a longpolling (gevent) worker for instant messenger and possibly other things. Unfortunately it doesn't work with `dev_mode`, which reloads python code as you change it. 

- For development — disable longpolling location in `odoo.conf` and add `dev_mode = True` to Odoo config file. 
- For staging — make sure `dev_mode` is disabled.
