FROM jmarin/jdk8:latest
MAINTAINER Juan Marin <juan.marin.otero@gmail.com>

RUN mkdir -p /usr/share/jenkins && wget http://mirrors.jenkins-ci.org/war/latest/jenkins.war -O /usr/share/jenkins/jenkins.war

EXPOSE 8080
CMD ["java", "-jar", "/usr/share/jenkins/jenkins.war"]

