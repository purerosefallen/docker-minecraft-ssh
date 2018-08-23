FROM ubuntu

RUN apt update
RUN apt install -y openssh-server locales curl git vim sudo tar gzip zip unzip cron net-tools build-essential p7zip-full screen byobu

# ssh
RUN ssh-keygen -q -N "" -t dsa -f /etc/ssh/ssh_host_dsa_key
RUN ssh-keygen -q -N "" -t rsa -f /etc/ssh/ssh_host_rsa_key

RUN mkdir -p /var/run/sshd
RUN mkdir /root/.ssh
RUN echo 'PermitRootLogin yes' >> /etc/ssh/sshd_config

# locale
RUN echo "zh_CN.UTF-8 UTF-8" > /etc/locale.gen && \
    ln -sf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime && \
    locale-gen && \
    dpkg-reconfigure -f noninteractive locales tzdata && \
    /usr/sbin/update-locale LANG=zh_CN.UTF-8
ENV LANG=zh_CN.UTF-8


# declarations
EXPOSE 22
VOLUME /root

WORKDIR /root
COPY entrypoint.sh /entrypoint.sh
RUN chmod +x /entrypoint.sh
CMD [ "/entrypoint.sh" ]
