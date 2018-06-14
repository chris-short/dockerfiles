FROM alpine:latest

LABEL maintainer="Chris Short <chris@chrisshort.net>"

RUN set -x \
        && apk update \
        && apk upgrade \
        && apk add --no-cache curl ca-certificates

ADD https://get.aquasec.com/microscanner .
RUN chmod +x microscanner
ARG token
RUN ./microscanner $token

ENTRYPOINT [ "/bin/sh", "-c" ]

CMD [ "/usr/bin/curl -vvv -H '${CONTTYPE}' -d '${DATA}' -X POST ${URL}" ]
