# Terminus

*terminus.crichon.eu*
This is the dev version of my vps.

Run:

    docker-compose up

All services should be available at http://$service_name.localdomain
All services use data container to persist configuration and data.

## Included

I use [jwilder/nginx] (http://github.com/jwilder/nginx) as a proxy.
It will automatically expose my docker services thgrouh nice urls as long as containers pops and dies.

Currently provided:
 - [circhon/subsonic](https://registery.hub.docker/u/crichon/subsonic) \*: media streamer
 - [crichon/selfoss]("https://registery.hub.docker/u/crichon/selfoss")\*: rss reader
 - [crichon/shaarli]("https://registery.docker.hub.com/u/crichon/shaarli")\*: save and share you links
 - [gitlab/gitlab-ce](https://registery.hub.docker.com/u/gitlab/gitlab-ce) gitlab instance
 - [gitlab/gitlab-runner](https://registery.hub.docker.com/u/gitlab/gitlab-ce) gitlab runner

**\* home made docker images**

## Notes

### Gitlab-ci

In order to use gitlab's now integrated CI server (since v8.0), you will need to uncoment
docker-compose.yml file last two entries **gitlab-runner and gitlab-runner-config**.

Assuming you have a running gitlab server, log in and go to admin -> ci -> runners and copy the registration token.
Edit the value of CITLAB_CI_TOKEN under gitlab-runner -> environments.

Run

    docker-compose up gitlab-runner
    docker exec $(docker ps | grep gitlab-runner | head -n 1 | awk '{print $1}') register -n

Enjoy

