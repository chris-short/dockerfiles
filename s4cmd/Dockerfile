FROM alpine:latest
LABEL maintainer="Chris Short <chris@chrisshort.net>"

RUN set -x \
        && apk update \
        && apk upgrade \
        && apk add --no-cache ca-certificates py-pip \
        && pip install --no-cache-dir s4cmd

ENTRYPOINT [ "s4cmd" ]