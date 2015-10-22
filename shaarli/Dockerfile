from php:apache
maintainer Christophe Richon <moi@crichon.eu>

RUN apt-get update && apt-get install -q -y ca-certificates wget unzip php5-json
RUN apt-get update && apt-get install -y \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libpng12-dev \
        && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
        && docker-php-ext-install gd
        RUN docker-php-ext-install mbstring

        RUN wget -O /usr/local/etc/php/php.ini https://raw.githubusercontent.com/php/php-src/master/php.ini-production
        RUN wget https://github.com/shaarli/Shaarli/archive/stable.zip && unzip stable.zip
        RUN mv Shaarli-stable/* .
                                RUN rm stable.zip && rm  -rf Shaarli-stable # also delete .travis and .gitignore

                                RUN chown -R www-data:www-data /var/www/html/

                                VOLUME /var/www/html/data
                                EXPOSE 80
