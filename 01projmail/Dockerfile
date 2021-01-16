FROM registry.access.redhat.com/ubi8/ubi:8.0
#USER  1001
RUN yum install -y sudo && yum install -y mailx && \
useradd -ms /bin/bash usermail -p 'UGFzc3dvcmQxCg==' && \
echo "usermail ALL=(root) NOPASSWD:ALL" > /etc/sudoers.d/usermail && \
chmod 0440 /etc/sudoers.d/usermail 
USER 1001
CMD bash -c "for i in {1..100}; do echo \$i; sleep 10; done"

