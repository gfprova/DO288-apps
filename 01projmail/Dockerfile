FROM registry.access.redhat.com/ubi7
#USER  1001
RUN yum install -y sudo && yum install -y mailx && yum install -y postfix && \
useradd -ms /bin/bash usertest01 && useradd -ms /bin/bash usertest02 &&\
chgrp -R 0 /var/spool && chmod -R g=u /var/spool && chmod -R o=u /var/spool && \
chown -R postfix.postdrop /var/spool/postfix/public && \
chown -R postfix.postdrop /var/spool/postfix/maildrop && \
mkfifo /var/spool/postfix/public/pickup
USER 1001
CMD bash -c "for i in {1..100}; do echo \$i; sleep 10; done"
