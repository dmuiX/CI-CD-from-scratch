FROM maven:3.9.9-amazoncorretto-17-debian-bookworm as builder

COPY /src /usr/src/app/src
COPY pom.xml /usr/src/app

RUN mvn -f /usr/src/app/pom.xml clean package

FROM eclipse-temurin:17.0.15_6-jre-ubi9-minimal

COPY --from=builder /usr/src/app/target/my-app-1.0-SNAPSHOT.jar /usr/app/myapp-1.0-SNAPSHOT.jar

ENTRYPOINT ["java", "-cp", "/usr/app/myapp-1.0-SNAPSHOT.jar", "com.mycompany.app.App"]
