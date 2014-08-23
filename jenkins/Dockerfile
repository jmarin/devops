FROM jmarin/jdk8:centos7
MAINTAINER Juan Marin <juan.marin.otero@gmail.com>

RUN mkdir -p /usr/share/jenkins && wget http://mirrors.jenkins-ci.org/war/latest/jenkins.war -O /usr/share/jenkins/jenkins.war

EXPOSE 8080
ADD jenkins.sv.conf /etc/supervisor/conf.d/
CMD ["supervisord", "-c", "/etc/supervisor/supervisor.conf"]
