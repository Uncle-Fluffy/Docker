FROM redhat/ubi9:latest
ENV container docker

# Set environemtn variable for subscription
ENV RHSM_USERNAME=tcarter528
ENV RHSM_PASSWORD=NULLRedHat1

# Install required packages
#RUN subscription-manager register --username tcarter528 --password NULLRedHat1 --auto-attach
RUN subscription-manager register --username ${RHSM_USERNAME} --password ${RHSM_PASSWORD} --auto-attach

RUN dnf update && \
    dnf install -y net-tools && \
    dnf install -y iputils && \
    dnf install -y traceroute && \
    dnf install -y mlocate && \
    dnf install -y java-1.8.0-openjdk.x86_64 && \
    subscription-manager unregister

CMD [ "updatedb" , "/bin/bash"]
# docker build -t rhel9-ansible .
# docker run -itd --rm --name rhel9-ansiblehost rhel9-ansible
# docker container ls
# docker exec -it 3d5edec129dd bash
# docker stop 3d5edec129dd