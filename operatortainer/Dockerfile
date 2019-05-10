FROM registry.access.redhat.com/ubi8/ubi

ENV OPERATOR=/usr/local/bin/ansible-operator \
    USER_UID=1001 \
    USER_NAME=ansible-operator\
    HOME=/opt/ansible

# Install python dependencies
RUN yum install -y platform-python-devel python3-inotify gcc python3-pip \
 && pip3 install --no-cache-dir --upgrade setuptools \
 && pip3 install --no-cache-dir ansible ansible-runner openshift ansible-runner-http idna==2.7 \
 && yum remove -y platform-python-devel gcc \
 && yum clean all \
 && rm -rf /var/cache/yum

# Install ansible-operator binary
RUN curl -LO https://github.com/operator-framework/operator-sdk/releases/download/v0.7.0/operator-sdk-v0.7.0-x86_64-linux-gnu \
 && mv operator-sdk-v0.7.0-x86_64-linux-gnu ${OPERATOR} \
 && chmod +x ${OPERATOR}

# Get the custom k8s_status module (someday this will be in a collection)
RUN curl -LO https://github.com/openshift/ocp-release-operator-sdk/blob/master/library/k8s_status.py \
 && mkdir -p /usr/share/ansible/openshift \
 && mv k8s_status.py /usr/share/ansible/openshift/

# Create the basic ansible.cfg
RUN mkdir -p /etc/ansible \
 && printf '[defaults]\n\
roles_path = /opt/ansible/roles\n\
library = /usr/share/ansible/openshift\n'\
localhost ansible_connection=local\n\
> /etc/ansible/ansible.cfg

# Ensure directory permissions are properly set
RUN mkdir -p ${HOME}/.ansible/tmp \
 && chown -R ${USER_UID}:0 ${HOME} \
 && chmod -R ug+rwx ${HOME} \
 && chmod g+rw /etc/passwd

# Create entrypoint
RUN printf '#!/bin/bash -e\n\
if ! whoami &>/dev/null; then\n\
  if [ -w /etc/passwd ]; then\n\
    echo "${USER_NAME:-runner}:x:$(id -u):$(id -g):${USER_NAME:-runner} user:${HOME}:/sbin/nologin" >> /etc/passwd\n\
  fi\n\
fi\n\
exec ${OPERATOR} run ansible --watches-file=/opt/ansible/watches.yaml $@\n'\
> /usr/local/bin/entrypoint \
 && chmod +x /usr/local/bin/entrypoint

ENTRYPOINT ["/usr/local/bin/entrypoint"]

USER 1001
