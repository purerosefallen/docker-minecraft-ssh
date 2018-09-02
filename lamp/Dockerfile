FROM tutum/lamp

RUN sed -i 's/archive.ubuntu.com/mirrors.aliyun.com/g' /etc/apt/sources.list
RUN apt update
RUN apt upgrade -y
RUN apt install -y openssh-server locales curl git vim sudo tar gzip zip unzip cron net-tools build-essential p7zip-full screen byobu

# ssh
RUN ssh-keygen -A
RUN mkdir -p /var/run/sshd
RUN mkdir /root/.ssh
RUN echo 'PermitRootLogin yes' >> /etc/ssh/sshd_config

# declarations
EXPOSE 22 80 3306
VOLUME /root

WORKDIR /root
COPY entrypoint.sh /entrypoint.sh
RUN chmod +x /entrypoint.sh
CMD [ "/entrypoint.sh" ]
