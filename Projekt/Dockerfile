# Użyj najnowszego obrazu Mavena
FROM maven:latest AS build

WORKDIR /Projekt
COPY pom.xml .
COPY src ./src  
RUN mvn clean package -DskipTests

# Użyj OpenJDK 20
FROM openjdk:20-jdk
WORKDIR /Projekt
COPY --from=build /Projekt/target/jobportal-0.0.1-SNAPSHOT.jar app.jar

EXPOSE 8080
ENTRYPOINT ["java", "-jar", "app.jar"]
