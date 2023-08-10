FROM openjdk:8-jdk-alpine

ARG artifact=target/currency-exchange.jar

WORKDIR /app

EXPOSE 8000

COPY ${artifact} app.jar

ENTRYPOINT ["java", "-jar", "app.jar"]
