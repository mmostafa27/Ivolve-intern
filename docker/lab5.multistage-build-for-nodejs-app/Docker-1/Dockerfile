FROM  maven:3.9.10-eclipse-temurin-17 AS build
WORKDIR /app
COPY . .
RUN mvn package   

FROM eclipse-temurin:17-jdk-alpine
WORKDIR /app
COPY --from=build /app/target/*.jar app.jar
CMD ["java","-jar","app.jar"]
EXPOSE 8080 
