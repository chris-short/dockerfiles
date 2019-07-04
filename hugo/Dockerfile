FROM registry.gitlab.com/pages/hugo:latest
LABEL maintainer="Chris Short <chris@chrisshort.net>"

RUN set -x \
      && apk update \
      && apk upgrade \
      && apk add --no-cache git ca-certificates

WORKDIR ${WORKDIR}
VOLUME  ${WORKDIR}
EXPOSE  1313
ENTRYPOINT [ "/hugo" ]
CMD [ "--help" ]