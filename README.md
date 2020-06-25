# wfe_speedtest

supporting files for the speedtest server on the WLAN Pi

## nginx installation

in progress...

## apache2 installation

requirements: apache2 and php.

```
sudo apt install apache2 php
sudo systemctl restart apache2
```

### apache2 setup

add and enable config in `sites-available`

`vim /etc/apache2/sites-available/speed.conf`:

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

### firewall setup

enable port 8080

ufw:

```
sudo ufw allow 8080
```

## app installation

### production

copy files in `/src` to `/var/www/speed`

```
mkdir /var/www/speed
cd <repo>/src
cp ./src/* /var/www/speed -r
```

### development

```
sudo ln -s /opt/wlanpi/wfe_speedtest/src /var/www/speed 
```

## file permissions

speedtest `.php` files require write access!

e.g. change permissions to `www-data`:

```
sudo chown -R www-data /var/www/speed/*
```
