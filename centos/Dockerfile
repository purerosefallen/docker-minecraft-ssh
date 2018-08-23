FROM centos

COPY Centos-7.repo /etc/yum.repos.d/CentOS-Base.repo
RUN yum install -y epel-release yum-utils openssh-server curl wget git vim sudo tar gzip zip unzip net-tools gcc gcc-c++ sqlite-devel readline-devel openssl-devel screen byobu crontabs

# ssh
RUN ssh-keygen -A
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
