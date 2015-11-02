# Selfoss Docker

## Presentation

[Selfoss](http://selfoss.aditu.de/) is *the multiprupose rss reader*.

In this directory you will find the dockerfile providing crichon/selfoss.
It's based on [php:apache](https://registry.hub.docker.com/_/php/)

## Usage

Just run:

    docker run --name selfoss crichon/selfoss:latest

Selfoss be available on http://localhost:80

If you prefer you can use the compose file in order to start an automatic reverse proxy.
It should then be available on http://selfoss.localdomain.

Build and run:

    docker build --name selfoss selfoss/
    docker run --name selfoss selfoss

## Details

**php:apache** use port 80 by default, refer to [its](https://registry.hub.docker.com/_/php/) documentation for details.

All data are contained inside the volume:

    /var/www/html/data

In order to persit configuration this image store *config.ini* file inside the data folder.
This file is then linked to the application root.

If you are using the compose file, data would be kept thanks to a data container (*check docker-compose.yml*).
