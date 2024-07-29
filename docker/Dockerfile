# Use a Maven image with JDK 20 for building the application
FROM maven:3.9.1-openjdk-20 AS build

# Set the working directory
WORKDIR /app

# Copy the pom.xml and source code into the container
COPY pom.xml .
COPY src ./src

# Package the application
RUN mvn clean package -DskipTests

# Use a JDK 20 runtime image for running the application
FROM openjdk:20-jdk-slim

# Set the working directory
WORKDIR /app

# Copy the JAR file from the build stage
COPY --from=build /app/target/shopping-cart-0.0.1-SNAPSHOT.jar ./shopping-cart.jar

# Expose the port the app runs on
EXPOSE 9090

# Command to run the application
ENTRYPOINT ["java", "-jar", "shopping-cart.jar"]
