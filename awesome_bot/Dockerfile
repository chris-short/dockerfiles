FROM alpine:latest
LABEL maintainer="Chris Short <chris@chrisshort.net>"

RUN set -x \
        && apk update \
        && apk upgrade \
        && apk add --no-cache ruby ruby-rdoc ruby-irb

RUN gem install awesome_bot

ENTRYPOINT ["awesome_bot"]
CMD ["--help"]