# tests2i
FROM registry.access.redhat.com/ubi8/ubi:8.0

# TODO: Put the maintainer name in the image metadata
# LABEL maintainer="Your Name <your@email.com>"

# TODO: Rename the builder environment variable to inform users about application you provide them
# ENV BUILDER_VERSION 1.0

# TODO: Set labels used in OpenShift to describe the builder image
LABEL io.k8s.description="Platform for building basic httpd " \
      io.k8s.display-name="builder myversion" \
      io.openshift.expose-services="8080:http" \
      io.openshift.s2i.scripts-url="image:///usr/libexec/s2i"

# Apache HTTP Server DocRoot
ENV DOCROOT /var/www/html
# TODO: Install required packages here:
RUN yum install -y nodocs --disableplugin=subscription-manager httpd && \
yum clean all --disableplugin=subscription-manager -y && \
echo "Iindex page from the my S2I builder image." > ${DOCROOT}/index.html

RUN sed -i "s/Listen 80/Listen 8080/g" /etc/httpd/conf/httpd.conf
# TODO (optional): Copy the builder files into /opt/app-root
# COPY ./<builder_folder>/ /opt/app-root/

# TODO: Copy the S2I scripts to /usr/libexec/s2i, since openshift/base-centos7 image
# sets io.openshift.s2i.scripts-url label that way, or update that label
COPY ./s2i/bin/ /usr/libexec/s2i

# TODO: Drop the root user and make the content of /opt/app-root owned by user 1001
# RUN chown -R 1001:1001 /opt/app-root

# This default user is created in the openshift/base-centos7 image
USER 1001

# TODO: Set the default port for applications built using this image
# EXPOSE 8080

# TODO: Set the default CMD for the image
# CMD ["/usr/libexec/s2i/usage"]
