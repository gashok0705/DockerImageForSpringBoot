# DockerImageForSpringBoot

# Start with a base image containing Java runtime
FROM openjdk:8-jdk-alpine

# Add Maintainer Info
LABEL maintainer="raj@abc.com"

# Add a volume pointing to /tmp
VOLUME /tmp

# Make port 9010 available to the world outside this container
EXPOSE 9010

# The application's jar file
ARG JAR_FILE=SpringBootHelloWorldRestApi-0.0.1-SNAPSHOT.jar

# Add the application's jar to the container
ADD $JAR_FILE springboot-demo.jar

# Run the jar file
ENTRYPOINT ["java","-Djava.security.egd=file:/dev/./urandom","-jar","/springboot-demo.jar"]

#The jar file and this file should be in the same location
#Running commands
#docker build -t newspring -f Dockerfile.txt . 
#docker run -d --name dynamicSpringBoot -P newspring 
#iptables -t nat -L
#Observe the ip & hit in the URL like this http://192.168.99.100:32778/
#response is // 20190516104043
#// http://192.168.99.100:32778/

#[
#  "rajagopal.ganesan@abc.com",
#  "response.ka@abc.com",
#  "response.k@abc.com"
#]
