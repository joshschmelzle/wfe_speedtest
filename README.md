# wfe_speedtest

## installation

Requires apache2 and php.

```
sudo apt install apache2 php
sudo systemctl restart apache2
```

## apache2 setup

add and enable config in `sites-available`

```
<VirtualHost *:8080>
	DocumentRoot /var/www/speed
	ErrorLog ${APACHE_LOG_DIR}/error.log
	CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
```

```
sudo a2dissite 000-default.conf
sudo a2ensite speed.conf
```

ensure apache2 is listening on respective port in `/etc/apache2/ports.conf`

```
Listen 8080
```

## firewall setup

enable port 8080

ufw:

```
sudo ufw allow 8080
```

## app 

#### method 1

copy files in `/src` to `/var/www/speed`

### method 2

```
sudo ln -s /opt/wlanpi/wfe_speedtest/src /var/www/speed 
```

speedtest requires write access. change permissions to `www-data`:

```
sudo chown -R www-data /var/www/speed/*
```
