# Installation #

  1. Upload all files in the ZIP archive
  1. make the directories `config, data/cache, data/favicons and data/thumbnails` writeable (use your FTP client and change the rights of the directories)
  1. open rsslounge in your browser and follow install instructions


# OPML Import #

The most RSS reader offers an OPML export. You can export all your feeds in a single XML File. This file can be imported in rsslounge. Open the menue on the header (right) and chose "OPML Import". rsslounge will import all feeds and reloads the page. Afterwards rsslounge will update all feeds. This first update needs a little bit more time than the further updates.

**Important:** The feed icons will be set after the first update of the feeds!


# Update via Cronjob #

For updating rsslounge feeds via cronjob point your cronjob to open
> `http://<rsslounge url>/update/silent`
via wget or curl.


# After installation all looks weird #

Mac OS and Linux users must ensure that all files will be uploaded. Also the file .htaccess which is hidden by default on Unix based Systems.


# Password protected rss feeds #

You can also subscribe to password protected rss feeds. Just enter the username and passwort before the url:
> `http://user:password@example.com/rss`


# The page is empty or following php error occurs #
> `PHP Parse error:  syntax error, unexpected T_CLASS in /home/bongzone/public_html/rsshat.com/application/models/settings.php on line 1`
Choose the binary upload in your FTP Client software.


# There are problems on the feed update process, where can I find more debug information? #

rsslounge offers an logging mechanism which can be activated via the configuration file
> `config/config.ini`
Change there the option
> `logger.level = ALERT`
to
> `logger.level = DEBUG`
Then you can find detailed information about an cronjob or ajax update in the log file:
> `data/logs/default`


# I only get an ServerError 500 #

This error occurs especially on Apache 1. Insert in the
> `.htaccess`
following line bellow "RewriteEngine on"
```
    RewriteEngine on
    RewriteBase /path/to/rsslounge/
```


# I don't see icons #

rsslounge tries to collect all favicons of your feeds in one single image file. This reduce the http requests on loading rsslounge dramaticaly. But the conversion of some ico files failed. You can disable the favicon collection by setting following parameter in the config/config.ini file:
> `cache.iconcaching = 0`
Then rsslounge will include the favicons directly (without generating one single image file).


# Installation on lighttpd #

For user of lighttpd you have to set the rewrite rules in the lighttpd configuration:

```
    url.rewrite-once = (
      "^/rsslounge/favicon.ico$" => "/rsslounge/public/favicon.ico",          
      "^/rsslounge/plugins/([^/]+)/(.*)$" => "/rsslounge/plugins/$1/public/$2",
      "^/rsslounge/favicons/(.*)$" => "/rsslounge/data/favicons/$1",
      "^/rsslounge/thumbnails/(.*)$" => "/rsslounge/data/thumbnails/$1",
      "^/rsslounge/javascript/(.*)$" => "/rsslounge/public/javascript/$1",    
      "^/rsslounge/stylesheets/(.*)$" => "/rsslounge/public/stylesheets/$1",  
      "^/rsslounge/public/" => "$0",                                   
      "^/rsslounge/(.*)" => "/rsslounge/index.php?mod_rewrite=1&$1"
    )
```

Modify the urls according to your directory structure.


# Installation on nginx #

For user of nginx you have to set the rewrite rules in the configuration:

```
    server {
        listen              80;
        server_name         www.server.com;

        root /var/www;
        index           index.php index.html index.htm;
        location ~ .php$ {
            root            /var/www;
            fastcgi_pass    unix:/tmp/php-fpm; # oder einfach 127.0.0.1:9000 je nach Einstellung
            include         fastcgi_params;
            fastcgi_param   QUERY_STRING   mod_rewrite=1&$query_string; # perfomanter als ein rewrite
            fastcgi_index   index.php;
            fastcgi_param   SCRIPT_FILENAME   $document_root$fastcgi_script_name;
        }
        # rewrites von .htaccess:
        rewrite ^/favicon.ico$ /public/favicon.ico;
        rewrite ^/plugins/([^/]+)/(.*)$ /plugins/$1/public/$2;
        rewrite ^/favicons/(.*)$ /data/favicons/$1;
        rewrite ^/thumbnails/(.*)$ /data/thumbnails/$1;
        rewrite ^/javascript/(.*)$ /public/javascript/$1;
        rewrite ^/stylesheets/(.*)$ /public/stylesheets/$1;

        location ~ \.htaccess {
            deny all;
        }

        if (!-e $request_filename) {
            rewrite ^.*$ /index.php last;
        }

    }
```