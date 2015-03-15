# Builds docker image for subsonic
FROM java:7

# Let the container know that there is no tty
ENV DEBIAN_FRONTEND noninteractive

# Set locale to UTF-8
ENV LANGUAGE en_US.UTF-8
ENV LANG en_US.UTF-8
ENV LC_ALL en_US.UTF-8

# Update Ubuntu
RUN apt-mark hold initscripts udev plymouth
RUN apt-get update && apt-get -qy dist-upgrade && apt-get -q update && apt-get install wget

# install subsonic
RUN wget http://downloads.sourceforge.net/project/subsonic/subsonic/sonos-beta/subsonic-5.1.deb -O /tmp/subsonic.deb
RUN dpkg -i /tmp/subsonic.deb && rm /tmp/subsonic.deb

# Transcoders
RUN ln /var/subsonic/transcode/ffmpeg /var/subsonic/transcode/lame /usr/local/bin

# Set user nobody to uid and gid of unRAID
RUN usermod -u 99 nobody
RUN usermod -g 100 nobody
RUN chown -R nobody:users /var/subsonic
RUN mkdir /subsonic && chown -R nobody:users /subsonic

USER nobody 
CMD /usr/bin/subsonic \
    --home=/subsonic \
    --host=0.0.0.0 \
    --https-port=4050 \
    --max-memory=200 \
    --default-music-folder=/music \
    --default-podcast-folder=/podcast \
    --default-playlist-folder=/playlist \
    && sleep 5 && tail -f /subsonic/subsonic_sh.log
