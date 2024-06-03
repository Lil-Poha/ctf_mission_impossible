FROM ubuntu:latest

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update && apt-get -y upgrade && apt-get install -y openssh-server 

RUN apt-get -y install apache2 php libapache2-mod-php

RUN apt-get -y install language-pack-ru && update-locale LANG=ru_RU.UTF-8

RUN apt-get -y install sudo net-tools vim nano openssh-server netcat-traditional wget iputils-ping curl language-pack-ru \
    && update-locale LANG=ru_RU.UTF-8

ARG ROOT_PASSWORD="crime"

ARG USERNAME="johny_crecker"

ARG USERNAME1="micke_snovy"

ARG USERNAME_PASSWORD="mission"

ARG USERNAME1_PASSWORD="svneopr"

RUN echo "root:${ROOT_PASSWORD}" | chpasswd

RUN groupadd -g 1000 ${USERNAME} && \
    useradd -s /bin/bash -u 1000 -g 1000 -m ${USERNAME} && \
    echo "${USERNAME}:${USERNAME_PASSWORD}" | chpasswd

RUN useradd -m -s /bin/bash $USERNAME1 && echo "${USERNAME1}:${USERNAME1_PASSWORD}" | chpasswd

RUN echo "$USERNAME1 ALL=(ALL) NOPASSWD: /usr/bin/cat" >> /etc/sudoers

COPY ./site/ /var/www/html/

EXPOSE 80

EXPOSE 22

COPY flag1.txt /home/johny_crecker/flag1.txt

COPY password.txt /home/johny_crecker/password.txt

COPY flag2.txt /home/micke_snovy/flag2.txt

COPY flag3.txt /root

COPY little_hint.txt /home/micke_snovy

#RUN service ssh start

#RUN service apache2 start
CMD service ssh start && apache2ctl -D FOREGROUND 