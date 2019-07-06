FROM registry.access.redhat.com/ubi8/nodejs-10:latest
LABEL maintainer="Chris Short <chris@chrisshort.net>"

RUN npm install -g firebase-tools

ENTRYPOINT [ "firebase" ]

CMD [ "--help" ]
