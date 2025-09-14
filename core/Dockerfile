FROM maven:3.9.6-eclipse-temurin-17 AS builder

WORKDIR /app

COPY pom.xml

RUN mvn -B dependency:go-offline

COPY . .

RUN mvn -B clean package -DskipTests

FROM eclipse-temurin:17-jdk

WORKDIR /app

COPY --from=builder /app/target/*.jar app.jar

EXPOSE 6060

CMD ["java", "-jar", "app.jar"]


