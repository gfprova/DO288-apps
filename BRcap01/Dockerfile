FROM registry.access.redhat.com/ubi8/ubi:8.0
USER 1001
CMD bash -c "x=1; while [ $x -le 10 ]; do (( x++ )); echo test \$x; sleep 10; done"
