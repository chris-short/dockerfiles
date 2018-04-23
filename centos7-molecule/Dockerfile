FROM centos:7

LABEL maintainer="Chris Short <chris@chrisshort.net>"

RUN set -x \
        && yum -y install epel-release \
        && yum clean all
RUN set -x \
        && yum -y install python-pip \
        && yum clean all
RUN set -x \
        && pip install --upgrade pip \
        && pip install virtualenv \
        ansible \
        ansible-lint \
        testinfra \
        molecule \
        docker-py

ENTRYPOINT [ "/bin/bash" ]

