FROM gallna/grunt-sass
MAINTAINER Tomasz Jonik <tomasz@hurricane.works>

RUN apt-get update

RUN apt-get install -y openssh-server
RUN mkdir /var/run/sshd

RUN echo 'root:root' |chpasswd

RUN sed -ri 's/^PermitRootLogin\s+.*/PermitRootLogin yes/' /etc/ssh/sshd_config
RUN sed -ri 's/UsePAM yes/#UsePAM yes/g' /etc/ssh/sshd_config

RUN apt-get install -y java7-jdk
RUN apt-get install -y git
RUN apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

VOLUME /www
WORKDIR /www
EXPOSE 22

CMD    ["/usr/sbin/sshd", "-D"]
