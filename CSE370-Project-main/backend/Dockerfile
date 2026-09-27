# Step 1: Build the application using Maven with Java 25
FROM maven:3.9-eclipse-temurin-25 AS build
WORKDIR /app
COPY . .

# Grant execute permission to the Maven wrapper
RUN chmod +x ./mvnw

RUN ./mvnw clean package -DskipTests

# Step 2: Run the application on Java 25 JRE/JDK
FROM eclipse-temurin:25-jre
WORKDIR /app
COPY --from=build /app/target/*.jar app.jar
EXPOSE 8080
ENTRYPOINT ["java", "-jar", "app.jar"]