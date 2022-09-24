FROM maven:3.8.6-jdk-11 as build

WORKDIR /opt/app

COPY pom.xml .

COPY src /opt/app

RUN mvn install -U

FROM adoptopenjdk/openjdk11:alpine-jre

WORKDIR /app

COPY --from=build /opt/app/target/studentsystem-0.0.1-SNAPSHOT.jar /app

#ARG JAR_FILE=/app/studentsystem-0.0.1-SNAPSHOT.jar

EXPOSE 8080

ENTRYPOINT ["java","-jar","/app/studentsystem-0.0.1-SNAPSHOT.jar"]

