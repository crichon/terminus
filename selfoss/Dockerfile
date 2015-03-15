from php:apache
maintainer Christophe Richon <moi@crichon.eu>

RUN apt-get update && apt-get install -q -y ca-certificates sqlite wget unzip php5-json php5-sqlite php5-gd

RUN wget  -O selfoss.zip http://selfoss.aditu.de/selfoss-2.12.zip
RUN unzip selfoss.zip && rm selfoss.zip
RUN a2enmod rewrite

# override basic configuration (edit it to your likings)
RUN sed s#base_url=#base_url=/# < defaults.ini | \
sed s#allow_public_update_access=#allow_public_update_access=1# | \
sed s#public=#public=1# > tmp && mv tmp defaults.ini
RUN mkdir -p /var/www/html/data/sqlite /var/www/html/data/cache /var/www/html/data/logs /var/www/html/data/thumbnails
RUN chown -R www-data:www-data /var/www/html
