FROM alpine:3.20.3

ARG USER_UID=${UID:-1000}
ARG USER_GID=${USER_GID:-$USER_UID}

RUN \
  apk add --no-cache zig=~0.12.0 git && \
  adduser -D -u ${USER_UID} newbie ${USER_GID} && \
  mkdir /ziglings /source && \
  chown -R newbie:newbie /ziglings /source

WORKDIR /ziglings
USER newbie

RUN \
  git clone --depth 1 --branch v0.12.0 https://codeberg.org/ziglings/exercises.git /source/exercises && \
  rm -rf /source/exercises/.git