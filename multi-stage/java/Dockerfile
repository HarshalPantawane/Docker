FROM maven:3.9-eclipse-temurin-17 as build 

WORKDIR /app

COPY pom.xml .
RUN mvn dependency:go-offline

COPY src ./src
RUN mvn clean package -DskipTests

# stage 2: create a smaller image with only the necessary files

FROM eclipse-temurin:17-jre

WORKDIR /app
COPY --from=build /app/target/*.jar app.jar

EXPOSE 8080
CMD [ "java", "-jar", "app.jar" ]

