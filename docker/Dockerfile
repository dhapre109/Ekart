# Use a Maven image with JDK 20 for building the application
FROM openjdk:8u151-jdk-alpine3.7

# Set the working directory
WORKDIR /app

# Copy the pom.xml and source code into the container
COPY pom.xml .
COPY src ./src

# Package the application
RUN mvn clean package -DskipTests

# Set the working directory
WORKDIR /app

# Expose the port the app runs on
EXPOSE 9090

# Command to run the application
ENTRYPOINT ["java", "-jar", "shopping-cart.jar"]
