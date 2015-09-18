from php:apache
maintainer Christophe Richon <moi@crichon.eu>

RUN apt-get update && apt-get install -q -y ca-certificates wget unzip php5-json

RUN wget -O /usr/local/etc/php/php.ini https://raw.githubusercontent.com/php/php-src/master/php.ini-production
RUN wget https://github.com/shaarli/Shaarli/archive/stable.zip && unzip stable.zip
RUN mv Shaarli-stable/* .
RUN rm stable.zip && rm  -rf Shaarli-stable # also delete .travis and .gitignore

RUN chown -R www-data:www-data /var/www/html/

VOLUME /var/www/html/data
EXPOSE 80
