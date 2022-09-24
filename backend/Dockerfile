FROM maven:3.6.3-jdk-11 as build

WORKDIR /opt/app

COPY pom.xml .

COPY . /opt/app

VOLUME ~/.m2 /root/.m2

RUN mvn install -Dmaven.test.skip=true

FROM adoptopenjdk/openjdk11:alpine-jre

WORKDIR /app

COPY --from=build /opt/app/target/studentsystem-0.0.1-SNAPSHOT.jar /app

#ARG JAR_FILE=/app/studentsystem-0.0.1-SNAPSHOT.jar

EXPOSE 8080

ENTRYPOINT ["java","-jar","/app/studentsystem-0.0.1-SNAPSHOT.jar"]

