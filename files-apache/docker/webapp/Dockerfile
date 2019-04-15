FROM amsdard/php-webapp:7

ENV WORKDIR=/opt

# build apache
COPY ./docker/webapp/000-default.conf /etc/apache2/sites-enabled/000-default.conf

# build data = the order do matter
RUN date > /builddate && chown 1000:1000 -R /opt

COPY ./vendor                       $WORKDIR/vendor
COPY ./src                          $WORKDIR/src
COPY --chown=1000:1000 ./app        $WORKDIR/app
COPY --chown=1000:1000 ./extensions $WORKDIR/extensions
COPY --chown=1000:1000 ./public     $WORKDIR/public

COPY ./.bolt.yml                    $WORKDIR
COPY ./composer.json                $WORKDIR
