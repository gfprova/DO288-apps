FROM registry.access.redhat.com/ubi8/ubi:8.0
#USER 1001
RUN yum install -y sudo && \
useradd -ms /bin/bash usermail && \
echo "usermail ALL=(root) NOPASSWD:ALL" > /etc/sudoers.d/usermail && \
chmod 0440 /etc/sudoers.d/usermail
