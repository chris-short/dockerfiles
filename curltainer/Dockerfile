FROM amazonlinux:2022

LABEL maintainer="Chris Short <chris@chrisshort.net>"

RUN set -x \
        && dnf update \
        && dnf upgrade \
        && dnf install curl ca-certificates \
        && dnf clean all

ENTRYPOINT [ "/bin/sh", "-c" ]

CMD [ "/usr/bin/curl -vvv -H '${CONTTYPE}' -d '${DATA}' -X POST ${URL}" ]
