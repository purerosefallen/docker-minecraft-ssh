FROM centos

RUN ssh-keygen -A
RUN yum install -y epel-release yum-utils openssh-server curl wget git vim sudo gcc gcc-c++ sqlite-devel readline-devel openssl-devel screen byobu crontabs

# ssh
RUN mkdir -p /var/run/sshd
RUN mkdir /root/.ssh
RUN echo 'PermitRootLogin yes' >> /etc/ssh/sshd_config

# declarations
EXPOSE 22
VOLUME /root

WORKDIR /root
COPY entrypoint.sh /entrypoint.sh
RUN chmod +x /entrypoint.sh
CMD [ "/entrypoint.sh" ]
