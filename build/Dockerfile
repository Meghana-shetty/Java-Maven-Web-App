FROM maven:latest AS build
WORKDIR /app
COPY . .
RUN mvn package -DskipTests

FROM tomcat:latest
WORKDIR /work
RUN rm -rf /usr/local/tomcat/webapps/*
COPY --from=build /app/target/*.war /usr/local/tomcat/webapps/new.war
EXPOSE 8080
CMD ["catalina.sh", "run"]
