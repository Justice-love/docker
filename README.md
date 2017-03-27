# docker
## DockerFile
```docker
FROM centos:7
MAINTAINER justice-love (eddyxu1213@126.com)
RUN cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime
ENV LANG en_US.UTF-8
ENV LANGUAGE en_US.UTF-8
ENV LC_ALL en_US.UTF-8
ADD jdk-8u121-linux-x64.rpm /usr/local/
ADD web-1.0-SNAPSHOT.jar /usr/local/web/
RUN rpm -ivh /usr/local/jdk-8u121-linux-x64.rpm
EXPOSE 8090
WORKDIR /usr/local/web/
ENTRYPOINT java -Dspring.profiles.active=pro -Dstock.im.token=mine_token -Dserver.port=8090 -Dstock.login.password=mine_passwd -Dlogging.path=/usr/local/web/logs -jar web-1.0-SNAPSHOT.jar
```
