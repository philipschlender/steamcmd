FROM philipschlender/ubuntu:latest

ARG GROUP=user
ARG USER=user

RUN set -e -u -x; \
    apt-get update; \
    apt-get install --no-install-recommends --yes ca-certificates curl lib32gcc-s1 lib32stdc++6 locales; \
    rm --force --recursive  /var/lib/apt/lists/*

RUN set -e -u -x; \
    sed --expression 's/# en_US.UTF-8 UTF-8/en_US.UTF-8 UTF-8/' --in-place /etc/locale.gen; \
    dpkg-reconfigure --frontend noninteractive locales; \
    mkdir --parents /home/${USER}/.steam/sdk32; \
    mkdir --parents /home/${USER}/.steam/sdk64; \
    mkdir --parents /home/${USER}/steamcmd; \
    curl --fail --location --output /home/${USER}/steamcmd/steamcmd.tar.gz --show-error --silent "https://steamcdn-a.akamaihd.net/client/installer/steamcmd_linux.tar.gz"; \
    tar --directory /home/${USER}/steamcmd --extract --gzip --file /home/${USER}/steamcmd/steamcmd.tar.gz; \
    rm /home/${USER}/steamcmd/steamcmd.tar.gz; \
    /home/${USER}/steamcmd/steamcmd.sh +quit; \
    ln --symbolic /home/${USER}/steamcmd/linux32/steamclient.so /home/${USER}/.steam/sdk32/steamclient.so; \
    ln --symbolic /home/${USER}/steamcmd/linux32/steamclient.so /home/${USER}/steamcmd/steamservice.so; \
    ln --symbolic /home/${USER}/steamcmd/linux32/steamcmd /home/${USER}/steamcmd/linux32/steam; \
    ln --symbolic /home/${USER}/steamcmd/linux64/steamclient.so /home/${USER}/.steam/sdk64/steamclient.so; \
    ln --symbolic /home/${USER}/steamcmd/linux64/steamclient.so /usr/lib/x86_64-linux-gnu/steamclient.so; \
    ln --symbolic /home/${USER}/steamcmd/linux64/steamcmd /home/${USER}/steamcmd/linux64/steam; \
    ln --symbolic /home/${USER}/steamcmd/steamcmd.sh /home/${USER}/steamcmd/steam.sh; \
    chown --recursive ${USER}:${GROUP} /home/${USER}/.steam; \
    chown --recursive ${USER}:${GROUP} /home/${USER}/steamcmd
