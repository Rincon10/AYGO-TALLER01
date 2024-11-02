# Compilando la aplicacion
# Use Maven with JDK 17 as the base image
FROM maven:3.8.5-openjdk-17 AS builder


# directorio de trabajo
WORKDIR /home/maven/app

## copiando depencn
COPY --chown=maven:maven pom.xml /home/maven/app

# Copy the rest of the project files
COPY . .

RUN ./mvnw clean package -DskipTests


FROM eclipse-temurin:17-jdk-jammy

WORKDIR /app

COPY --from=builder /home/maven/app/target/myapp-1.0-SNAPSHOT.jar /app/myapp-1.0-SNAPSHOT.jar

ENTRYPOINT ["java", "-jar","myapp-1.0-SNAPSHOT.jar"]