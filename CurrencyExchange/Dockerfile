FROM openjdk:8-jdk-alpine
ARG artifact=target/currency-exchange.jar
WORKDIR /app
COPY ${artifact} app.jar
ENTRYPOINT ["java","-jar","app.jar"]