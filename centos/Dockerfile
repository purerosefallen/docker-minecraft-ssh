FROM centos

RUN ssh-keygen -A
RUN yum install -y epel-release yum-utils openssh-server curl wget git vim sudo tar zip unzip gcc gcc-c++ sqlite-devel readline-devel openssl-devel screen byobu crontabs

# ssh
RUN ssh-keygen -q -N "" -t dsa -f /etc/ssh/ssh_host_dsa_key
RUN ssh-keygen -q -N "" -t rsa -f /etc/ssh/ssh_host_rsa_key

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
