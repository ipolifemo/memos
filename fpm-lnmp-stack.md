## mysql

```
sudo apt-get install -y mysql-server php5-mysql
sudo mysql_install_db
sudo /usr/bin/mysql_secure_installation
```

## nginx

```
echo "deb http://ppa.launchpad.net/nginx/stable/ubuntu $(lsb_release -sc) main" | sudo tee /etc/apt/sources.list.d/nginx-stable.list
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys C300EE8C
sudo apt-get update
sudo apt-get install nginx
# sudo service nginx start
# ifconfig eth0 | grep inet | awk '{ print $2 }'
```

## php-fpm

```
sudo apt-get install php5-fpmi
```

### configure
```
#vi /etc/php5/fpm/php.ini`
cgi.fix_pathinfo=0`
```
Tell nginx to not process the file that is as near to the requested file as possible

```
# /etc/php5/fpm/pool.d/www.conf
listen = /var/run/php5-fpm.sock
```


