###  Força a utilizar Cache-Control e Expires header
```
#Força a utilizar Cache-Control e Expires header
<IfModule mod_headers.c>
Header unset ETag
</IfModule>
 FileETag None
<IfModule mod_expires.c>
ExpiresActive on
ExpiresDefault "access plus 1 month"
ExpiresByType text/cache-manifest "access plus 0 seconds"
# Html
ExpiresByType text/html "access plus 0 seconds"
# Data
ExpiresByType text/xml "access plus 0 seconds"
ExpiresByType application/xml "access plus 0 seconds"
ExpiresByType application/json "access plus 0 seconds"
# Feed
ExpiresByType application/rss+xml "access plus 1 hour"
ExpiresByType application/atom+xml "access plus 1 hour"
# Favicon
ExpiresByType image/x-icon "access plus 1 week"
# Media: images, video, audio
ExpiresByType image/gif "access plus 1 month"
ExpiresByType image/png "access plus 1 month"
ExpiresByType image/jpg "access plus 1 month"
ExpiresByType image/jpeg "access plus 1 month"
ExpiresByType video/ogg "access plus 1 month"
ExpiresByType audio/ogg "access plus 1 month"
ExpiresByType video/mp4 "access plus 1 month"
ExpiresByType video/webm "access plus 1 month"
# HTC files
ExpiresByType text/x-component "access plus 1 month"
# Webfonts
ExpiresByType application/x-font-ttf "access plus 1 month"
ExpiresByType font/opentype "access plus 1 month"
ExpiresByType application/x-font-woff "access plus 1 month"
ExpiresByType image/svg+xml "access plus 1 month"
ExpiresByType application/vnd.ms-fontobject "access plus 1 month"
# CSS / JS
ExpiresByType text/css "access plus 1 year"
ExpiresByType application/javascript "access plus 1 year"
ExpiresByType application/x-javascript "access plus 1 year"
</IfModule>
#Força o IE a sempre carregar utilizando a última versão disponível
<IfModule mod_headers.c>
Header set X-UA-Compatible "IE=Edge,chrome=1"
<FilesMatch "\.(js|css|gif|png|jpeg|pdf|xml|oga|ogg|m4a|ogv|mp4|m4v|webm|svg|svgz|eot|ttf|otf|woff|ico|webp|appcache|manifest|htc|crx|oex|xpi|safariextz|vcf)$" >
Header unset X-UA-Compatible
</FilesMatch>
</IfModule>
# Enf Força a utilizar Cache-Control e Expires header
```	
