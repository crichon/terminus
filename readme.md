# Selfoss Docker

## Presentation

[Selfoss](http://selfoss.aditu.de/) is *the multiprupose rss reader*.

In this directory you will find the dockerfile providing crichon/selfoss.
It's based on [php:apache](https://registry.hub.docker.com/_/php/)

## Usage

Just run:

    docker run --name selfoss crichon/selfoss:latest

Build and run:

    git clone http://github.com/crichon/terminus.git && cd treminus && git co selfoss
    docker build --name selfoss selfoss/
    docker run --name selfoss selfoss

## Details

**php:apache** use port 80 by default, refer to [its](https://registry.hub.docker.com/_/php/) documentation for details.

All data are contained inside the volume:

    /var/www/html/data

In order to persit configuration this image store *config.ini* file inside the data folder.
This file is then linked to the application root.

