FROM redhat/ubi8:8.10
ENV container docker

# Set environemtn variable for subscription
ENV RHSM_USERNAME=tcarter528
ENV RHSM_PASSWORD=NULLRedHat1

# Install required packages
#RUN subscription-manager register --username tcarter528 --password NULLRedHat1 --auto-attach
RUN subscription-manager register --username ${RHSM_USERNAME} --password ${RHSM_PASSWORD} --auto-attach

RUN dnf update
RUN dnf install -y sudo
RUN dnf install -y wget
RUN dnf install -y vim
RUN dnf install -y net-tools

RUN dnf install -y openssh-server
RUN ssh-keygen -t rsa -f /etc/ssh/ssh_host_rsa_key -N ''
RUN ssh-keygen -t ecdsa -f /etc/ssh/ssh_host_ecdsa_key -N ''
RUN ssh-keygen -t ed25519 -f /etc/ssh/ssh_host_ed25519_key -N ''
RUN ssh-keygen -t rsa -b 2048 -N "" -f ~/.ssh/id_rsa
RUN cat /root/.ssh/id_rsa.pub >> /root/.ssh/authorized_keys
RUN cat /root/.ssh/authorized_keys
RUN /usr/sbin/sshd
#RUN ps -ef | grep sshd
RUN systemctl enable sshd
EXPOSE 22

RUN dnf install -y bind-utils
RUN dnf install -y iputils
RUN dnf install -y traceroute
RUN dnf install -y mlocate 
RUN dnf install -y procps-ng

RUN dnf install -y firewalld
RUN dnf install -y java-1.8.0-openjdk.x86_64
RUN dnf install -y ansible-core
RUN subscription-manager unregister
COPY ansible/ /home/tcarter/
#COPY ssh/ /root/.ssh/

RUN updatedb

#CMD ["/bin/bash"]
CMD ["/usr/sbin/sshd", "-D"]
#CMD ["/usr/sbin/init"]
# docker build --no-cache -t rhel8-ansible .
# docker build --progress=plain --no-cache -t rhel8-ansible . > build.log 2>&1
# docker build --progress=plain --no-cache -t rhel8-ansible . | tee build.log 2>&1
# docker run -itd --rm --name rhel8-ansiblehost rhel8-ansible
# docker container ls
# docker exec -it 3d5edec129dd bash
# docker stop 3d5edec129dd