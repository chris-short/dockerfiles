FROM registry.access.redhat.com/ubi8/ubi-minimal
LABEL maintainer="Chris Short <chris@chrisshort.net>"

RUN set -x \
      && microdnf update -y \
      && microdnf install -y ca-certificates curl tar gzip git file libtool \
      && microdnf clean all \
      && rm -rf /var/cache/yum

ENTRYPOINT [ "bash" ]