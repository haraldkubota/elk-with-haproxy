# ELK+HAproxy

See https://hkubota.wordpress.com/2020/02/11/elk-with-https/ for a more detailed explanation what's going on here.

## How to use this

### Requirements

* A Linux machine with docker and docker-compose
* 2 GB RAM at least
* A valid TLS certificate (put into haproxy/ssl/private/YOUR_HOST_AND_DOMAIN.pem)

Note that the certificate must contain the actual certificate and the private key with no passphrase. Otherwise HAproxy cannot use it.

### Usage

Edit haproxy.cfg with a new admin password (replace ADMINPW with something less known.)
Adjust the external ports in the haproxy section in docker-compose.yml to match your open firewall ports.

Change the owner of the data/ directory and start the containers with
```
chown 991:991 data
docker-compose up -d
```

At this point you have a insecure (no accounts, no password) ELK _with HTTPS_. To add accounts, follow the instructions from https://hkubota.wordpress.com/2020/02/11/elk-with-https/
