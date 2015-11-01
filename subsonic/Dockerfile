# Builds docker image for subsonic
FROM java:7

# Let the container know that there is no tty
ENV DEBIAN_FRONTEND noninteractive

# Update Ubuntu
RUN apt-mark hold initscripts udev plymouth
RUN apt-get update && apt-get -qy dist-upgrade
RUN apt-get -q update && apt-get -qy install locales
RUN echo "en_US.UTF-8 UTF-8" > /etc/locale.gen && locale-gen

# Set locale to UTF-8
ENV LANGUAGE en_US.UTF-8
ENV LANG en_US.UTF-8
ENV LC_ALL en_US.UTF-8

# install subsonic
ADD http://subsonic.org/download/subsonic-5.3.deb /tmp/subsonic.deb
RUN dpkg -i /tmp/subsonic.deb && rm /tmp/subsonic.deb

# Transcoders
RUN ln /var/subsonic/transcode/ffmpeg /var/subsonic/transcode/lame /usr/local/bin

# Set user nobody to uid and gid of unRAID
RUN mkdir /subsonic /music

RUN echo ''' \
useradd $user && chown -R $user:$group /music \
''' > /bin/fix_user.sh && chmod +x /bin/fix_user.sh

VOLUME /subsonic
CMD grep $user /etc/passwd || /bin/fix_user.sh \
    && /usr/bin/subsonic \
    --home=/subsonic \
    --host=0.0.0.0 \
    --https-port=4050 \
    --max-memory=200 \
    --default-music-folder=/music \
    --default-podcast-folder=/podcast \
    --default-playlist-folder=/playlist \
    && sleep 5 && tail -f /subsonic/subsonic_sh.log
#usermod -u $user_id $user \
#usermod -g $group_id $group \
