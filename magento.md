Use the git mirror to get releases

```
git clone https://github.com/OpenMage/magento-mirror.git
```

Export releases

```
cd magento-mirror
git archive --format=tar.gz --prefix=magento <release tag> > magento-<release>.tar.gz
```

Configure nginx site:

```
# /etc/nginx/sites-enabled/magento
server {
    listen      80;
    server_name store.local;
    root        $PROJECTS_PATH/magento/;
    access_log  /var/log/nginx/magento-access_log;
    error_log   /var/log/nginx/magento-error_log;

	location / {
        index index.php;
        if ($request_uri ~* "\.(ico|css|js|gif|jpe?g|png)$") {
            access_log off;
            expires max;
        }
        try_files $uri $uri/ @handler;
    }

    location /app/                       { deny all; }
    location /includes/                  { deny all; }
    location /lib/                       { deny all; }
    location /media/downloadable/        { deny all; }
    location /pkginfo/                   { deny all; }
    location /report/config.xml          { deny all; }
    location /var/                       { deny all; }
	location /lib/minify/ 		         { allow all; }

    location /var/export/ {
        auth_basic              "Restricted";
        auth_basic_user_file    htpasswd;
        autoindex               on;
    }

	location @handler {
        rewrite ^(.*) /index.php?$1 last;
    }

	fastcgi_intercept_errors on;

	location ~ \.php$ {
		fastcgi_split_path_info ^(.+\.php)(/.+)$;

    	include fastcgi_params;
		fastcgi_param   SCRIPT_FILENAME    $document_root$fastcgi_script_name;
        fastcgi_param   SCRIPT_NAME        $fastcgi_script_name;

    	fastcgi_index index.php;
    	fastcgi_pass unix:/var/run/phpfpm.sock;
	}
}
```

Development tools

Pre-reqs:
```
sudo apt-get install -y php5-cli
```

Cli tools for magento:

```
wget http://files.magerun.net/n98-magerun-latest.phar -O n98-magerun.phar
chmod +x ./n98-magerun.phar
```
