FROM registry.access.redhat.com/rhel7-atomic:latest

LABEL maintainer="Chris Short <chris@chrisshort.net>"

RUN set -x \
        && yum update \
        && yum upgrade \
        && yum install git s3cmd ca-certificates

ENTRYPOINT [ "s3cmd" ]