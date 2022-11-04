FROM public.ecr.aws/docker/library/fedora:latest

LABEL maintainer="Chris Short <chris@chrisshort.net>"

RUN yum -y update \
	&& yum -y install java git curl \
	&& yum clean all

RUN cd \
	&& curl -O https://repo1.maven.org/maven2/com/madgag/bfg/1.14.0/bfg-1.14.0.jar

RUN rm -rf /usr/share/doc/* \
	&& rm -rf /usr/share/info/* \
	&& rm -rf /tmp/* \
	&& rm -rf /var/tmp/*


ENTRYPOINT [ "/bin/bash" ]
