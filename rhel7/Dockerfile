FROM jvalance/ubi7:7.7
ENV container docker

# Set environemtn variable for subscription
ENV RHSM_USERNAME=tcarter528
ENV RHSM_PASSWORD=NULLRedHat1

# Install required packages
#RUN subscription-manager register --username tcarter528 --password '-6BkHNqZLfcc$m6' --auto-attach
RUN subscription-manager register --username ${RHSM_USERNAME} --password ${RHSM_PASSWORD} --auto-attach

RUN subscription-manager repos --enable rhel-7-server-ansible-2.9-rpms

RUN yum install -y ansible.noarch && \
    yum install -y net-tools && \
    yum install -y iproute && \
    yum install -y iputils && \
    yum install -y traceroute && \
    yum install -y java-1.8.0-openjdk.x86_64 && \
    yum install -y mlocate \
    yum clean all  && \
    subscription-manager unregister && \
    subscription-manager clean

CMD [ "updatedb" , "/usr/sbin/init"]

# docker build -t rhel7-ansible .
# docker run -itd --network newasguard --ip 192.168.2.3 --name rhel7-ansiblehost rhel7-ansible
 