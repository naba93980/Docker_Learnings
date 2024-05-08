
# Use a base image
FROM maven:3.9.6-amazoncorretto-17 AS buildHotelService

# Set the working directory
WORKDIR /home/HotelService

# Copy the source code to the container
COPY . .

# Install dependencies
# RUN microdnf install -y maven

# Set Maven path
# ENV PATH="/usr/share/maven/bin:${PATH}"

# Build the app
RUN --mount=type=cache,target=/root/.m2,rw mvn clean package

# Use a base image
FROM amazoncorretto:17-alpine3.18-jdk

COPY --from=buildHotelService /home/HotelService/target/Hotel-Service-1.0.0.jar /home/HotelService/Hotel-Service-1.0.0.jar

EXPOSE 8081

# Specify the command to run the app
ENTRYPOINT [ "java", "-jar", "/home/HotelService/Hotel-Service-1.0.0.jar"]
