FROM alpine:latest
LABEL maintainer="Chris Short <chris@chrisshort.net>"

RUN set -x \
        && apk update \
        && apk upgrade \
        && apk add --no-cache ca-certificates py-pip \
        && pip install s3cmd

ENTRYPOINT [ "s3cmd" ]