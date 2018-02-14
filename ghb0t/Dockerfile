FROM alpine
LABEL maintainer="Chris Short <chris@chrisshort.net>"

COPY ghb0t-linux-arm /usr/local/bin/ghb0t

RUN set -x \
    && apk update \
    && apk upgrade \
    && apk add ca-certificates

ENTRYPOINT [ "/usr/local/bin/ghb0t" ]
CMD [ "--help" ]