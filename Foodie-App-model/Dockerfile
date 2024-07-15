#FROM ubuntu:latest
#LABEL authors="sreekanth0807"
#
#ENTRYPOINT ["top", "-b"]


# Use an official Ubuntu as a parent image
FROM ubuntu:latest

# Install necessary dependencies
RUN apt-get update && apt-get install -y \
    openjdk-22-jdk \
    maven

# Set the working directory
WORKDIR /app

# Copy the parent pom.xml file and the source code
COPY pom.xml /app
COPY src /app/src

# Package the application
RUN mvn clean package -DskipTests

# Define environment variables
ENV SPRING_CONFIG_LOCATION=/app/application.properties

# Run the application
CMD ["java", "-jar", "/app/target/foodie-app.jar"]
# Replace 'your-app.jar' with the actual jar name


