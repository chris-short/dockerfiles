FROM registry.access.redhat.com/ubi8/ubi-minimal
LABEL maintainer="Chris Short <chris@chrisshort.net>"

RUN set -x \
      && microdnf update -y \
      && microdnf install -y ca-certificates curl tar gzip git file libtool \ 
      which sudo \
      && microdnf clean all \
      && rm -rf /var/cache/yum \
      && useradd --no-log-init -G wheel homebrew

USER homebrew

RUN set -x \
      && curl -fsSL https://raw.githubusercontent.com/Linuxbrew/install/master/install.sh

ENTRYPOINT [ "bash" ]