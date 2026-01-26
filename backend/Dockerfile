FROM eclipse-temurin:17-jdk-alpine

WORKDIR /app

COPY /target/my_server.jar /app/my_server.jar

EXPOSE 8080

ENTRYPOINT [ "java", "-jar", "my_server.jar" ]