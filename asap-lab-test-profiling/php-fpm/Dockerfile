FROM php:fpm

# add test script
COPY ["www-data/test.php", "/var/www/html/"]

# add-install profiler with dependency to image
RUN apt-get update && \
    apt-get install -y \
    graphviz

COPY ["profiler/xhprof-2.3.7.tgz", "/tmp"]

RUN cd /tmp && \
    mkdir -p /var/xhprof && \
    tar xf ./xhprof-2.3.7.tgz -C /var/xhprof && \
    cd /var/xhprof/xhprof-2.3.7/extension && \
    phpize && \
    ./configure && \
    make && \
    make install

COPY profiler/xhprof.ini /usr/local/etc/php/conf.d/xhprof.ini

RUN docker-php-ext-enable xhprof

#folder for xhprof profiles
RUN mkdir -p -m 777 /profiles
