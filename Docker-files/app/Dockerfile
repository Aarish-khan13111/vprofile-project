FROM openjdk:11 as BUILD_IMAGE
LABEL "project"="vprofile"
LABEL "Auther"="Aarish"
RUN apt update && apt install maven -y
RUN git clone https://github.com/Aarish-khan13111/vprofile-project.git
RUN cd vprofile-project && git checkout docker && mvn install

FROM tomcat:9-jre11
RUN rm -rf /usr/local/tomcat/webapps/*
COPY --from=BUILD_IMAGE vprofile-project/target/vprofile-v2.war  /usr/local/tomcat/webapps/Root.war

EXPOSE 8080
CMD [ "catalina.sh", "run"]