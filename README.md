Change Memory Limit in 

/usr/local/etc/php/conf.d/php.ini


// Push new image
1. Tag it
example: docker tag apachephpcomposerimage_web:latest oppamh/apache-php-composer:php_7.4
2. login to dockerhub
docker login docker.io
3. push
docker push oppamh/apache-php-composer:php_7.4
