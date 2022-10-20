FROM nginx:latest

# add default site conf for tested script
COPY nginx/default.conf /etc/nginx/conf.d/default.conf

# add testeed script to image
COPY ["www-data/test.php", "/var/www/html/"]

# add site conf for profiler web ui
COPY nginx/xhprof.conf /etc/nginx/conf.d/xhprof.conf

COPY ["profiler/xhprof-2.3.7.tgz", "/tmp"]

RUN cd /tmp && \
    mkdir -p /var/xhprof && \
    tar xf ./xhprof-2.3.7.tgz -C /var/xhprof


