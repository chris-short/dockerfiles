FROM registry.access.redhat.com/ubi8/ubi-minimal
LABEL maintainer="Chris Short <chris@chrisshort.net>"

RUN set -x \
      && microdnf update -y \
      && microdnf install -y ca-certificates curl
      && microdnf clean all \
      && rm -rf /var/cache/yum \

RUN set -x \
      && curl -o ossutil http://gosspublic.alicdn.com/ossutil/1.6.1/ossutil64 \
      && chmod 0755 ossutil

ENTRYPOINT [ "ossutil help" ]