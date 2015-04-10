# Shaarli Docker

## Presentation

[Shaarli](http://sebsauvage.net/wiki/doku.php?id=php:shaarli)

> a minimalist delicious clone you can install on your own website. It is designed to be personal (single-user), fast and handy.

In this directory you will find the dockerfile providing crichon/shaarli.
Based on [php:apache](https://registry.hub.docker.com/_/php/)

## Usage

Just run:

    docker run --name shaarli crichon/shaarli:latest

Build and run:

    git clone http://github.com/crichon/terminus.git && cd treminus && git co shaarli
    docker build --name selfoss selfoss/
    docker run --name selfoss selfoss

## Details

**php:apache** use port 80 by default, refer to [its](https://registry.hub.docker.com/_/php/) documentation for details.

All data are contained inside the volume:

    /var/www/html/data
