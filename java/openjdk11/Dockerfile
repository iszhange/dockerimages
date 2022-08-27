FROM openjdk:11

RUN sed -i "s/deb.debian.org/mirrors.163.com/g" /etc/apt/sources.list \ 
    && sed -i "s/security.debian.org/mirrors.163.com/g" /etc/apt/sources.list \
    && apt-get update \ 
    && apt-get install -y vim
