FROM registry.access.redhat.com/ubi8/ubi:8.0
ENV X_SCLS="nginx" \
PATH="/usr/sbin/nginx:$PATH" \
NGINX_DOCROOT="/usr/share/nginx/html"
LABEL io.k8s.description="A Nginx S2I builder image" \
io.k8s.display-name="Nginx 1.8 S2I builder image for DO288" \
io.openshift.expose-services="8080:http" \
io.openshift.s2i.scripts-url="image:///usr/libexec/s2i" \
io.openshift.tags="builder,webserver,nginx,html"
ADD nginxconf.sed /tmp/
COPY ./.s2i/bin/ /usr/libexec/s2i
RUN yum install -y nginx \
&& yum clean all \
&& sed -i -f /tmp/nginxconf.sed /etc/nginx/nginx.conf \
&& chgrp -R 0 /etc/nginx \
&& chmod -R g=u /etc/nginx \
&& echo 'Hello from the Nginx S2I builder image' > ${NGINX_DOCROOT}/index.html
EXPOSE 8080
USER 1001
CMD ["/usr/libexec/s2i/usage"]
