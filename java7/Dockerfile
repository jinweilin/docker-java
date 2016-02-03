FROM ubuntu:14.04
MAINTAINER Jinwei <jinwei.lin@gmail.com>

RUN apt-get update
RUN apt-get install -y wget

ENV java_version 1.7.0_79
ENV filename jdk-7u79-linux-i586.tar.gz
ENV downloadlink http://download.oracle.com/otn-pub/java/jdk/7u79-b15/$filename

# download java, accepting the license agreement
RUN wget --no-cookies --header "Cookie: oraclelicense=accept-securebackup-cookie" -O /tmp/$filename $downloadlink 

# unpack java
RUN mkdir /opt/java-oracle && tar -zxf /tmp/$filename -C /opt/java-oracle/
ENV JAVA_HOME /opt/java-oracle/jdk$java_version
ENV PATH $JAVA_HOME/bin:$PATH

# configure symbolic links for the java and javac executables
RUN update-alternatives --install /usr/bin/java java $JAVA_HOME/bin/java 20000 && update-alternatives --install /usr/bin/javac javac $JAVA_HOME/bin/javac 20000
