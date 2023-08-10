# Stage 1: Build your project using Maven image
FROM maven:3.8.4-openjdk-11 AS build

# Set your working directory
WORKDIR /app

# Copy the Maven project file
COPY pom.xml .

# Build the project (dependencies will be cached)
RUN mvn dependency:go-offline

# Copy the rest of the application code
COPY src/ /app/src/

# Build the application
RUN mvn package

# Stage 2: Create a smaller image with only necessary components
FROM openjdk:11-jre-slim

# Set the working directory
WORKDIR /app

# Copy the compiled JAR file from the build stage
COPY --from=build /app/target/your-app.jar .

# Install Docker CLI
RUN apt-get update && apt-get install -y --no-install-recommends docker.io && rm -rf /var/lib/apt/lists/*

# Container entry point
CMD ["java", "-jar", "your-app.jar"]
