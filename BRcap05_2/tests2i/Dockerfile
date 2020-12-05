#FROM registry.redhat.io/rhel8/httpd-24
FROM registry.access.redhat.com/ubi8/ubi:8.0
# Add application sources
ENV DOCROOT /var/www/html
RUN yum install -y --nodocs --disableplugin=subscription-manager httpd && \
yum clean all --disableplugin=subscription-manager -y && \
echo "This is the default index page from the s2i-do288-httpd S2I builder image." > ${DOCROOT}/index.html
RUN sed -i "s/Listen 80/Listen 8080/g" /etc/httpd/conf/httpd.conf
COPY ./s2i/bin/ /usr/libexec/s2i
#ADD app-src/index.html /var/www/html/index.html

# The run script uses standard ways to run the application
CMD run-httpd
