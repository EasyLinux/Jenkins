FROM openjdk:8-jdk-alpine
LABEL author="Serge NOEL <serge.noel@net6a.com>" \
      Description="This is a base image, which provides the Jenkins agent executable"

RUN mkdir /usr/share/jenkins
WORKDIR /usr/share/jenkins
RUN wget http://mirrors.jenkins.io/war-stable/latest/jenkins.war
RUN addgroup -g 1000 jenkins
RUN adduser -h /var/jenkins_home -u 1000 -G jenkins -D jenkins

ADD jenkins.war /usr/share/jenkins/jenkins.war
RUN apk add --update --no-cache bash git openssh-client openssl procps ttf-dejavu \
  && chmod 755 /usr/share/jenkins
RUN chmod 644 /usr/share/jenkins/jenkins.war

USER jenkins
#ENV WORKDIR=/var/jenkins_home
#RUN mkdir /var/jenkins_home/.jenkins && mkdir -p ${AGENT_WORKDIR}

VOLUME /var/jenkins_home
#VOLUME ${AGENT_WORKDIR}
WORKDIR /var/jenkins_home

#USER root
CMD ["/usr/bin/java","-jar","/usr/share/jenkins/jenkins.war"]
