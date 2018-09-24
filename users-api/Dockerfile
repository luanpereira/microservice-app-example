FROM openjdk:8-alpine

EXPOSE 8083 8787
WORKDIR /usr/src/app


COPY pom.xml mvnw ./
COPY .mvn/ ./.mvn
RUN sed -i 's/\r$//' mvnw
RUN ./mvnw dependency:resolve

COPY . .
RUN sed -i 's/\r$//' mvnw
RUN ./mvnw install

CMD ["java", "-agentlib:jdwp=transport=dt_socket,server=y,suspend=n,address=8787", "-jar", "./target/users-api-0.0.1-SNAPSHOT.jar"]
