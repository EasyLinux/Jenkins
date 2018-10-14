FROM openjdk:8-jdk-alpine
LABEL author="Serge NOEL <serge.noel@net6a.com>" \
      Description="This is a base image, which provides the Jenkins agent executable"

RUN addgroup -g 1000 jenkins
RUN adduser -h /var/jenkins_home -u 1000 -G jenkins -D jenkins

ADD slave.jar /usr/share/jenkins/slave.jar
RUN apk add --update --no-cache bash git openssh-client openssh-server openssl procps \
  && chmod 755 /usr/share/jenkins \
  && chmod 644 /usr/share/jenkins/slave.jar

USER jenkins
ENV AGENT_WORKDIR=/var/jenkins_home
#RUN mkdir /var/jenkins_home/.jenkins && mkdir -p ${AGENT_WORKDIR}

VOLUME /var/jenkins_home
#VOLUME ${AGENT_WORKDIR}
WORKDIR /var/jenkins_home


