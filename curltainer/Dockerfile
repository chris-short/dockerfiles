FROM public.ecr.aws/docker/library/fedora:latest

LABEL maintainer="Chris Short <chris@chrisshort.net>"

RUN set -x \
        && dnf update -y \
        && dnf upgrade -y \
        && dnf install curl ca-certificates -y \
        && dnf clean all

ENTRYPOINT [ "/bin/sh", "-c" ]

CMD [ "/usr/bin/curl -vvv -H '${CONTTYPE}' -d '${DATA}' -X POST ${URL}" ]
