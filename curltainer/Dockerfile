FROM alpine:latest

LABEL maintainer="Chris Short <chris@chrisshort.net>"

RUN set -x \
        && apk update \
        && apk upgrade \
        && apk add --no-cache curl ca-certificates

ENTRYPOINT [ "/bin/sh", "-c" ]

CMD [ "/usr/bin/curl -vvv -H '${CONTTYPE}' -d '${DATA}' -X POST ${URL}" ]
