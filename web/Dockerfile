FROM ubuntu:latest
RUN apt-get -y update && apt-get -y upgrade
RUN apt-get  install openjdk-11-jre-headless  wget -y
RUN mkdir /usr/local/tomcat
RUN wget https://dlcdn.apache.org/tomcat/tomcat-8/v8.5.85/bin/apache-tomcat-8.5.85.tar.gz -O /tmp/tomcat.tar.gz
RUN cd /tmp && tar xvfz tomcat.tar.gz
RUN cp -Rv /tmp/apache-tomcat-8.5.85/* /usr/local/tomcat/
RUN ls /usr/local/tomcat/
RUN wget https://s3-us-west-2.amazonaws.com/studentapi-cit/student.war
ADD https://tomcat-war-jar-new.s3.amazonaws.com/mysql-connector.jar /usr/local/tomcat/lib
RUN cp -Rv student.war /usr/local/tomcat/webapps/
COPY ./data.txt /usr/local/tomcat/ 
RUN sed '20r /usr/local/tomcat/data.txt' -i /usr/local/tomcat/conf/context.xml 
EXPOSE 8080
CMD ["/usr/local/tomcat/bin/catalina.sh", "run"]

