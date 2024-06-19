#FROM ubuntu:latest

#
#ENTRYPOINT ["top", "-b"]

# Use the official Maven image to create a build artifact.
# As a build step
# Use an official Ubuntu as a parent image
FROM ubuntu:latest

# Set the working directory
WORKDIR /app

# Install necessary dependencies
RUN apt-get update && apt-get install -y \
    openjdk-22-jdk \
    maven

# Copy the source code
COPY src /app/src
COPY pom.xml /app

# Package the application
RUN mvn -f /app/pom.xml clean package -DskipTests

# Copy the application properties
COPY application.properties /app/application.properties

# Define environment variables
ENV SPRING_CONFIG_LOCATION=/app/application.properties

# Run the application
CMD ["java", "-jar", "/app/target/eureka-server-0.0.1-SNAPSHOT.jar"]

