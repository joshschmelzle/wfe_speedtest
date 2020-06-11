# wfe_speedtest

## installation

Requires apache2 and php.

```
sudo apt install apache2 php
```

## apache2 setup

add and enable config in `sites-available`

ensure apache2 is listening on respective port in `/etc/apache2/ports.conf`

## app 

copy files in `/src` to `/var/www/html`

speedtest requires write access. change permissions to `www-data`:

```
sudo chown -R www-data /var/www/html/*
```
