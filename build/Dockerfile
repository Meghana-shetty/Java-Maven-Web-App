# important!!!!!!!! check pom.xml in that source/target if its 1.8 then that means it uses java 8 which we can package/compile with maven:latest but if there is nothing mentioned as source/target, then it defauls to java 7 which can't run with maven:latest as maven:latest will have java 17. So, better to use Java 11(3.9.0-eclipse-temurin-11) which supports all java versions

# important to remember
# JDK 8, 11, 17, 21 are available. 
# If pom.xml DOES NOT mention Java version → use Maven JDK 11
# If pom.xml DOES mention Java version → use a Maven image with the SAME JDK or HIGHER
# Java in pom.xml	Allowed Maven JDK
# 8	              8, 11, 17, 21
# 11	            11, 17, 21
# 17	            17, 21
# If pom.xml does NOT mention Java version → use JDK 11

FROM maven:3.9.0-eclipse-temurin-11 AS build
WORKDIR /app
COPY . .
RUN mvn package -DskipTests

FROM tomcat:latest
#WORKDIR /work not need 
RUN rm -rf /usr/local/tomcat/webapps/*
COPY --from=build /app/target/*.war /usr/local/tomcat/webapps/new.war
EXPOSE 8080
CMD ["catalina.sh", "run"]
