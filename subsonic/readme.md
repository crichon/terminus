# Subsonic Docker

## Presentation

[Subsonic](http://subsonic.org)

> a web based media player.

In this directory you will find the dockerfile providing crichon/subsonic.
Based on [java:7](https://registry.hub.docker.com/_/java/)

## Usage

Just run:

    docker run --name subsonic -v -p 443:4050 {your_music_dir}:/music subsonic /crichon/subsonic:latest

Build and run:

    git clone http://github.com/crichon/terminus.git && cd treminus && git co subsonic
    docker build --name subsonic subsonic/
    docker run --name subsonic  -p 443:4050 -v {your_music_dir}:/music subsonic

## Details

    VIRTUAL_PORTS: "4040", "4050"
    VIRTUAL_PROTO: "https"

All subsonic data are contained inside the volume:

    /subsonic

Mount your music and podcast host directory on /music and /podcast.
