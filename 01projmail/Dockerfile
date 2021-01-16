FROM registry.access.redhat.com/ubi8/ubi:8.0
USER usermail
RUN yum install -y sudo && \
useradd -ms /bin/bash usermail && \
echo "usermail ALL=(root) NOPASSWD:ALL" > /etc/sudoers.d/usermail && \
#echo "1001 ALL=(root) NOPASSWD:ALL" > /etc/sudoers.d/1001 && \
chmod 0440 /etc/sudoers.d/usermail
#chmod 0440 /etc/sudoers.d/1001
#CMD ["su", "-", "user", "-c", "/bin/bash"]
CMD bash -c "for i in {1..100}; do echo \$i; sleep 10; done"

