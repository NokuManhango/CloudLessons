# Start from an official OpenJDK image
FROM --platform=linux/amd64 eclipse-temurin:17-jdk

# Set the working directory in the container
WORKDIR /app

# Copy the Maven build files
COPY pom.xml .
COPY src ./src
COPY flight.sql ./flight.sql

# Package the application
RUN apt-get update && apt-get install -y maven
RUN mvn clean package -DskipTests

# Expose the port your Spring Boot app runs on
EXPOSE 8080

# Run the Spring Boot application
ENTRYPOINT ["java", "-jar", "target/flightservices-0.0.1-SNAPSHOT.jar"]