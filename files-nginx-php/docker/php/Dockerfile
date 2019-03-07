FROM amsdard/php:7

RUN docker-php-ext-install exif

ENV WORKDIR=/opt

# build data = the order do matter
RUN date > /builddate && chown 1000:1000 -R /opt

COPY ./vendor                       $WORKDIR/vendor
COPY ./src                          $WORKDIR/src
COPY --chown=1000:1000 ./app        $WORKDIR/app
COPY --chown=1000:1000 ./extensions $WORKDIR/extensions
COPY --chown=1000:1000 ./public     $WORKDIR/public

COPY ./.bolt.yml                    $WORKDIR
COPY ./composer.json                $WORKDIR