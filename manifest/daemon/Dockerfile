FROM node:8-alpine

MAINTAINER Cameron Carney <ccarney16@live.com>

ARG VERSION

ENV DAEMON_VERSION=${VERSION} \
    UID=500

WORKDIR /srv/daemon

RUN \
 apk --update --no-cache add coreutils curl openssl make gcc g++ python gnupg tar git \
 && git clone https://github.com/Mystical-Machines/daemon.git\
 && npm install --production \
 && addgroup -S -g ${UID} pterodactyl && adduser -S -D -H -G pterodactyl -u ${UID} -s /bin/false pterodactyl \
 && apk del curl make gcc g++ python gnupg \
 && rm -rf /root/.npm /root/.node-gyp /root/.gnupg \
 /var/cache/apk/* /tmp/*

EXPOSE 8080

CMD [ "npm", "start" ]
