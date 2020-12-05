FROM prova01
LABEL "io.openshift.s2i.build.source-location"="test/test-app" \
      "io.k8s.display-name"="prova01-test" \
      "io.openshift.s2i.build.image"="prova01"

USER root
# Copying in source code
COPY upload/src /tmp/src
# Change file ownership to the assemble user. Builder image must support chown command.
RUN chgrp -R 0 /tmp/src && chmod -R g=u /tmp/src && chgrp -R 0 /usr && chmod -R g=u /usr
USER 1001
# Assemble script sourced from builder image based on user input or image metadata.
# If this file does not exist in the image, the build will fail.
RUN /usr/libexec/s2i/assemble
# Run script sourced from builder image based on user input or image metadata.
# If this file does not exist in the image, the build will fail.
CMD /usr/libexec/s2i/run
