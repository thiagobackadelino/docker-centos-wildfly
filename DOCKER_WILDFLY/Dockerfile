FROM centos:latest

MAINTAINER thiagobackadelino <thiagobackadelino@gmail.com>

RUN yum install deltarpm sudo -y \

&& yum update -y \

&& yum install java-1.8.0-openjdk -y \

&& mkdir -p /opt/wildfly

WORKDIR /opt/wildfly

COPY wildfly-10.0.0.Final.tar.gz /opt/wildfly

RUN tar zxvf wildfly-10.0.0.Final.tar.gz \
&& useradd -s /usr/sbin/nologin wildfly \
&& chown -R wildfly /opt/wildfly/wildfly-10.0.0.Final

USER root 
 
RUN /opt/wildfly/wildfly-10.0.0.Final/bin/add-user.sh admin admin --silent

CMD ["/opt/wildfly/wildfly-10.0.0.Final/bin/standalone.sh", "-b", "0.0.0.0", "-bmanagement", "0.0.0.0"]

EXPOSE 8080 9990