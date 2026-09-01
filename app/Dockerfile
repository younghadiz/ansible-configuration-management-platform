FROM eclipse-temurin:17-jre-alpine

WORKDIR /opt/app

COPY build/libs/*.jar application.jar

EXPOSE 8080

USER 10001

ENTRYPOINT ["java", "-jar", "/opt/app/application.jar"]