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

## Compose details

Provide a runnging instance on http://music.localdomain and access to your music dir through a **samba share**.
Launch using:

    docker-compose up

Mount it using:

    mount -t cifs //samba.localdomain/music -o domain=WORKGROUP,user=user,ver=2.0 #passwd user

Configuration is done through modifying services *env variables* sections. Edit them to your likings.

Subsonic data are contained inside the  following volumes:

    /subsonic
    /music
    /podcast

