# Letsencrypt

## Install

`sudo apt install certbot`

## Generating a wildcard SSL certificate

Here is the error you will get if you persevere with a `webroot` challenge: 

⚠️ 
`Client with the currently selected authenticator does not support any combination of challenges that will satisfy the CA. You may need to use an authenticator plugin that can do challenges over DNS.
`

The challenge cannot be `webroot`, it has to be DNS-based for wildcard certificates.

`sudo certbot certonly --manual --preferred-challenges dns --server https://acme-v02.api.letsencrypt.org/directory --manual-public-ip-logging-ok -d *.domain.app -d domain.app`
