# -------- Stage 1 : Build --------
FROM maven:3.9.6-eclipse-temurin-17 AS builder

WORKDIR /build

COPY pom.xml .
RUN mvn -B dependency:go-offline

COPY src ./src
RUN mvn clean package -DskipTests


# -------- Stage 2 : Runtime (distroless) --------
FROM gcr.io/distroless/java17-debian11

WORKDIR /app

COPY --from=builder /build/target/*.jar app.jar

EXPOSE 8080

ENTRYPOINT ["java","-jar","/app/app.jar"]
