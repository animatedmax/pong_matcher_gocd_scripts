# DOCKER-VERSION 1.2.0

# base
FROM    ubuntu:14.10
RUN     apt-get update
RUN     apt-get install -qy build-essential wget

# create user
RUN     adduser --disabled-password web

# cf
ADD     https://cli.run.pivotal.io/stable?release=debian64&source=github cf.deb
RUN     dpkg -i cf.deb

# install java and maven
RUN     apt-get install -y openjdk-8-jdk
RUN 	apt-get install -y maven

# install app as unprivileged user
ADD         app pong_matcher
RUN         chown -R web:web pong_matcher

USER        web
ENV         JAVA_HOME /usr/lib/jvm/java-8-openjdk-amd64

RUN         cd pong_matcher; mvn -e package
