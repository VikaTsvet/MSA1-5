FROM maven:3.8.4-openjdk-17 as app_builder
WORKDIR /monolit
COPY . /monolit/.
RUN mvn -f /monolit/pom.xml clean package -Dmaven.test.skip=true

FROM eclipse-temurin:17-jre-alpine
COPY --from=app_builder /monolit/target/*.jar /monolit/*.jar
ENTRYPOINT ["java", "-jar", "/monolit/*.jar"]