# important!!!!!!!! check pom.xml in that source/target if its 1.8 then that means it uses java 8 which we can package/compile with maven:latest but if there is nothing mentioned as source/target, then it defauls to java 7 which can't run with maven:latest as maven:latest will have java 17. So, better to use Java 11(3.9.0-eclipse-temurin-11) which supports all java versions

FROM maven:3.9.0-eclipse-temurin-11 AS build
WORKDIR /app
COPY . .
RUN mvn package -DskipTests

FROM tomcat:latest
WORKDIR /work
RUN rm -rf /usr/local/tomcat/webapps/*
COPY --from=build /app/target/*.war /usr/local/tomcat/webapps/new.war
EXPOSE 8080
CMD ["catalina.sh", "run"]
