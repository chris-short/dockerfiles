FROM registry.access.redhat.com/ubi8/ubi-minimal
LABEL maintainer="Chris Short <chris@chrisshort.net>"

RUN set -x \
      && microdnf update -y \
      && microdnf install -y ca-certificates curl file gzip git libtool patch tar which \
      && microdnf clean all \
      && rm -rf /var/cache/yum \
      && useradd --no-log-init -G wheel linuxbrew

USER linuxbrew

RUN set -x \
      && yes | sh -c "$(curl -fsSL https://raw.githubusercontent.com/Linuxbrew/install/master/install.sh)"

ENTRYPOINT [ "/home/linuxbrew/.linuxbrew/bin/brew" ]