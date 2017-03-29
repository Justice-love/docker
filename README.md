# docker
## DockerFile
```docker
FROM centos:7
MAINTAINER justice-love (eddyxu1213@126.com)
RUN cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime
RUN echo 'Asia/Shanghai' > /etc/timezone
ENV LANG en_US.UTF-8
ENV LANGUAGE en_US.UTF-8
ENV LC_ALL en_US.UTF-8
ADD jdk-8u121-linux-x64.rpm /usr/local/
ADD web-1.0-SNAPSHOT.jar /usr/local/web/
RUN rpm -ivh /usr/local/jdk-8u121-linux-x64.rpm
EXPOSE 8090
WORKDIR /usr/local/web/
ENV TOKEN token
ENV PORT 8090
ENV LOG_DIR /usr/local/web/logs
ENV PASSWD pwd
ENV PROFILE pro
CMD java -Dspring.profiles.active=${PROFILE} -Dstock.im.mainToken=${TOKEN} -Dserver.port=${PORT} -Dlogging.path=${LOG_DIR} -Dstock.login.password=${PASSWD} -jar web-1.0-SNAPSHOT.jar

```
