FROM  maven:3.9.6-eclipse-temurin-21-alpine as builder

COPY . .

RUN mvn dependency:resolve

RUN mvn package

FROM eclipse-temurin:21-jre-alpine

COPY --from=builder /target/worker-jar-with-dependencies.jar .

CMD ["java", "-jar", "/target/worker-jar-with-dependencies.jar"]