FROM nginx:1

# build config
COPY docker/nginx/global /etc/nginx/global
COPY docker/nginx/default.conf /etc/nginx/conf.d/default.conf

# build data
ENV WORKDIR=/opt
RUN date > /builddate
COPY ./public $WORKDIR/public

# build nginx
