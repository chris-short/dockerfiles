FROM registry.access.redhat.com/ubi8/ubi-minimal
LABEL maintainer="Chris Short <chris@chrisshort.net>"

RUN set -x \
      && microdnf update -y \
      && microdnf install -y ca-certificates curl tar gzip git file libtool which \
      && microdnf clean all \
      && rm -rf /var/cache/yum \
      && useradd --no-log-init -G wheel homebrew

USER homebrew

RUN set -x \
      && curl -fsSL https://raw.githubusercontent.com/Linuxbrew/install/master/install.sh \
      && test -d ~/.linuxbrew && eval $(~/.linuxbrew/bin/brew shellenv) \
      && test -d /home/linuxbrew/.linuxbrew && eval $(/home/linuxbrew/.linuxbrew/bin/brew shellenv) \
      && test -r ~/.bash_profile && echo "eval \$($(brew --prefix)/bin/brew shellenv)" >>~/.bash_profile \
      && echo "eval \$($(brew --prefix)/bin/brew shellenv)" >>~/.bash_profile

ENTRYPOINT [ "bash" ]