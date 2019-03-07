FROM amsdard/php-webapp:7

ENV WORKDIR=/opt

# build apache
COPY ./docker/webapp/000-default.conf /etc/apache2/sites-enabled/000-default.conf

# build data = the order do matter
RUN date > /builddate && mkdir $WORKDIR/var && chown 1000:1000 -R /opt
COPY ./vendor $WORKDIR/vendor
COPY ./bin $WORKDIR/bin
COPY ./templates $WORKDIR/templates
COPY ./translations $WORKDIR/translations
COPY ./config $WORKDIR/config
COPY ./public $WORKDIR/public
COPY ./src $WORKDIR/src
COPY ./composer.json $WORKDIR
