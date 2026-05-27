FROM maven:3.8-eclipse-temurin-17 AS build-stage
WORKDIR /app
COPY pom.xml .
COPY src ./src
RUN mvn clean package -DskipTests

FROM eclipse-temurin:17-jdk-jammy
WORKDIR /app
COPY --from=build-stage /app/target/*.jar app.jar
EXPOSE 8082
CMD ["java", "-jar", "app.jar"]