FROM registry.access.redhat.com/ubi8/ubi-minimal
LABEL maintainer="Chris Short <chris@chrisshort.net>"

RUN set -x \
      && microdnf update -y \
      && microdnf groupinstall 'Development Tools'
      && microdnf install -y ca-certificates curl tar git file \
      && microdnf clean all \
      && rm -rf /var/cache/yum

ENTRYPOINT [ "bash" ]