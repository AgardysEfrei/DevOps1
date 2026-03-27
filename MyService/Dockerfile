FROM gradle:9.3.1-jdk-25-and-25 AS build
WORKDIR /app
COPY build.gradle settings.gradle ./
RUN gradle build --no-daemon -x test

FROM eclipse-temurin:25-jre AS run
WORKDIR /app
COPY --from=build /app/build/libs/*.jar app.jar
EXPOSE 8080
CMD ["java", "-jar", "app.jar"]
