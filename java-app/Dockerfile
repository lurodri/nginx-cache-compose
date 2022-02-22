FROM maven:3.8.4-jdk-8 AS builder
WORKDIR /usr/src/app
COPY pom.xml .
COPY . .
RUN mvn clean install

# Use an official OpenJDK runtime as a parent image
FROM openjdk:8-jre-alpine

# source: https://stackoverflow.com/a/40944512/3128926
RUN apk update 
RUN apk upgrade

# Set the working directory to /app
WORKDIR /app

# Copy the fat jar into the container at /app
#COPY --from=builder /usr/src/app/target/docker-java-app-example.jar /app
COPY --from=builder /usr/src/app/target/java-app.jar /app

# Make port 8080 available to the world outside this container
EXPOSE 8080

# Run jar file when the container launches
CMD ["java", "-jar", "java-app.jar"]
