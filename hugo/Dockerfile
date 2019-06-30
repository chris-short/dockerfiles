FROM registry.access.redhat.com/ubi8/ubi-minimal
LABEL maintainer="Chris Short <chris@chrisshort.net>"

RUN set -x \
      && microdnf update -y \
      && microdnf install -y ca-certificates curl file gzip git libtool tar which \
      && microdnf clean all \
      && rm -rf /var/cache/yum \
      && useradd --no-log-init -G wheel homebrew

USER homebrew

RUN set -x \
      && yes | sh -c "$(curl -fsSL https://raw.githubusercontent.com/Linuxbrew/install/master/install.sh)"

RUN set -x \
      && test -d ~/.linuxbrew && eval $(~/.linuxbrew/bin/brew shellenv)

RUN set -x \
      && test -d /home/linuxbrew/.linuxbrew && eval $(/home/linuxbrew/.linuxbrew/bin/brew shellenv)

RUN set -x \
      && test -r ~/.bash_profile && echo "eval \$($(brew --prefix)/bin/brew shellenv)" >>~/.bash_profile
RUN set -x \
      && echo "eval \$($(brew --prefix)/bin/brew shellenv)" >>~/.bash_profile

ENTRYPOINT [ "bash" ]