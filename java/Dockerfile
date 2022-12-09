FROM maven:3.8-openjdk-8 as builder

WORKDIR /usr/src/app

COPY . .

RUN mvn clean package -DskipTests=true


FROM openjdk:18-jdk

LABEL maintener="Tom SCHOUMACHER"

EXPOSE 8448

WORKDIR usr/src/app

COPY --from=builder usr/src/app/target/java-*.jar examPolytech2022.jar

CMD ["java", "-jar", "examPolytech2022.jar"]
