FROM registry.redhat.io/rhel8/httpd-24
# Add application sources
#COPY ./index.html /var/www/html/index.html

# The run script uses standard ways to run the application
#CMD run-httpd
RUN rm -f /usr/libexec/s2i/assemble
COPY ./index.html /tmp/src/index.html
COPY ./s2i/bin/assemble /usr/libexec/s2i/
RUN chgrp -R 0 /tmp/src /var/www/html && chmod -R g=u /tmp/src /var/www/html
USER 1001

#
## Let the assemble script install the dependencies
RUN /usr/libexec/s2i/assemble
#
## The run script uses standard ways to run the application
CMD /usr/libexec/s2i/run
