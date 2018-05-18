FROM centos:7

MAINTAINER Chris Short <chris@chrisshort.net>

ENV BFG_VER 1.13.0

RUN yum -y install java git curl

RUN yum -y update \
	&& yum clean all

RUN curl -o bfg.jar http://repo1.maven.org/maven2/com/madgag/bfg/${BFG_VER}/bfg-${BFG_VER}.jar \
	&& mv bfg.jar /usr/local/bin/

RUN rm -rf /usr/share/doc/* \
	&& rm -rf /usr/share/info/* \
	&& rm -rf /tmp/* \
	&& rm -rf /var/tmp/*

WORKDIR /tmp

#CMD ["java", "-jar", "/usr/local/bin/bfg.jar"]
ENTRYPOINT [ "/bin/bash" ]