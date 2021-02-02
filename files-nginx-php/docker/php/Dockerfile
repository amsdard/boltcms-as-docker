FROM amsdard/php:7

RUN docker-php-ext-install exif

ENV WORKDIR=/opt

COPY ./bin              $WORKDIR/bin
COPY ./config           $WORKDIR/config
COPY ./public           $WORKDIR/public
COPY ./src              $WORKDIR/src
COPY ./translations     $WORKDIR/translations
COPY ./vendor           $WORKDIR/vendor

COPY ./.bolt.yml        $WORKDIR
COPY ./composer.json    $WORKDIR

# build data = the order do matter
RUN date > /builddate && mkdir $WORKDIR/var && chown 1000:1000 -R $WORKDIR
