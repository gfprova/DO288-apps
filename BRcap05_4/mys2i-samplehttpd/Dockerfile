FROM prova-httpd
LABEL "io.k8s.display-name"="mys2i-samplehttpd" \
      "io.openshift.s2i.build.image"="prova-httpd" \
      "io.openshift.s2i.build.source-location"="test/test-app"

USER root
# Copying in source code
COPY upload/src /tmp/src
# Change file ownership to the assemble user. Builder image must support chown command.
RUN chown -R 1001:0 /tmp/src
#USER 1001
# Assemble script sourced from builder image based on user input or image metadata.
# If this file does not exist in the image, the build will fail.
RUN chgrp -R 0 /usr/libexec/s2i && chmod -R g+rwx /usr/libexec/s2i
USER 1001
RUN /usr/libexec/s2i/assemble
# Run script sourced from builder image based on user input or image metadata.
# If this file does not exist in the image, the build will fail.
CMD /usr/libexec/s2i/run
