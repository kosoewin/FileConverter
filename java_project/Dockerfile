FROM ubuntu:18.04
MAINTAINER soewin
RUN apt update && \
    apt-get -y install openjdk-8-jdk wget
RUN apt-get install -y openssh-server
RUN adduser user && usermod -aG sudo user
USER user
RUN mkdir -p /home/user/.ssh
RUN wget https://downloads.apache.org/tomcat/tomcat-8/v8.5.93/bin/apache-tomcat-8.5.93.tar.gz -O /tmp/tomcat.tar.gz
RUN cd /tmp ; tar -xzf tomcat.tar.gz
RUN mv /tmp/apache-tomcat-8.5.93/ /home/user/
RUN chmod -R 775 /home/user/*
COPY ./FileConverter.war /home/user/apache-tomcat-8.5.93/webapps/
RUN mkdir -p /home/user/Uploads
RUN mkdir -p /home/user/Uploads/EXCEL
RUN mkdir -p /home/user/Uploads/XML
ENV JAVA_OPTS="-Xms512m -Xmx512m"
EXPOSE 8080
CMD ["/home/user/apache-tomcat-8.5.93/bin/catalina.sh", "run"]
