FROM registry.access.redhat.com/ubi7
#USER  1001
RUN yum install -y sudo && yum install -y mailx && yum install -y sendmail &&\
useradd -ms /bin/bash usermail && \
chgrp -R 0 /var/spool && chmod g=u /var/spool
USER 1001
CMD bash -c "for i in {1..100}; do echo \$i; sleep 10; done"

