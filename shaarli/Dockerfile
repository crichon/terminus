from php:apache
maintainer Christophe Richon <moi@crichon.eu>

RUN apt-get update && apt-get install -q -y ca-certificates wget unzip php5-json

RUN wget https://github.com/sebsauvage/Shaarli/archive/master.zip \
&& unzip master.zip \
&& mv Shaarli-master/* . \
&& rm master.zip && rm -rf Shaarli-master

RUN mkdir /var/www/html/data && chown -R www-data:www-data /var/www/html/

VOLUME /var/www/html/data 
EXPOSE 80
