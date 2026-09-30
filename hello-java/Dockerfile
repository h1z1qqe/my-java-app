# Этап 1: сборка
FROM maven:3.9-eclipse-temurin-17 AS builder
WORKDIR /build
COPY pom.xml .
COPY src ./src
RUN mvn clean package -DskipTests

# Этап 2: запуск
FROM eclipse-temurin:17-jre-alpine
WORKDIR /app
COPY --from=builder /build/target/hello-java.jar app.jar
ENTRYPOINT ["java", "-jar", "app.jar"]
