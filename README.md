# spring-boot-rest-api-docker
application.properties;
server.port=8085

docker-compose :
version: '3'

services:
  spring-boot-jpa-app:
    image: spring-boot-rest-docker-image
    build:
      context: ./
      dockerfile: Dockerfile
    ports:
      - 8087:8085
    volumes:
      - /data/spring-boot-app
      
dockerfile:
FROM openjdk:8-jre
LABEL maintainer=“chathuranga.t@gmail.com”
WORKDIR /app
COPY target/spring-boot-rest-api-docker-0.0.1-SNAPSHOT.jar /app/spring-boot-app.jar
EXPOSE 8085
ENTRYPOINT ["java","-jar","spring-boot-app.jar"]


for below windows10 laptop check this link to map the virtual box for portforwarding to the docker container:
https://stackoverflow.com/questions/27471688/how-to-access-tomcat-running-in-docker-container-from-browser/27481832#27481832
