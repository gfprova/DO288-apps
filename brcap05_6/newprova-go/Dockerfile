FROM registry.access.redhat.com/ubi8/ubi:8.0
LABEL Component="go" Name="newprova-go" \
Version="1.0" Release="1"

LABEL io.k8s.description="A basic go S2I builder image" \
io.k8s.display-name="GO S2I builder image for DO288" \
io.openshift.expose-services="8080:http" \
io.openshift.s2i.scripts-url="image:///usr/libexec/s2i" \
io.openshift.tags="builder, go, golang"
WORKDIR /var/home/core/DO288-apps/brcap05_6/newprova-go
ENV APP_ROOT=/opt/app-root XDG_CACHE_HOME=off
RUN mkdir /usr/libexec/s2i/
RUN yum install -y --nodocs --disableplugin=subscription-manager golang && \
yum clean all --disableplugin=subscription-manager -y
#ADD ./s2i/bin/. /usr/libexec/s2i/
COPY ./s2i/bin/. /usr/libexec/s2i/
COPY ./s2i/bin/. $APP_ROOT
RUN mkdir -p $APP_ROOT && \
chown -R 1001:0 $APP_ROOT && \
chgrp -R 0 $APP_ROOT && \
chgrp -R 0 /usr/libexec/s2i && \
chmod -R g=u $APP_ROOT && \
chmod -R g=u /usr/libexec/s2i

USER 1001

EXPOSE 8080

WORKDIR $APP_ROOT

CMD ["usage"]
