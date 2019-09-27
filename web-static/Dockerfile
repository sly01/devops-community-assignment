FROM maven:latest AS builder

RUN git clone https://github.com/spring-projects/spring-boot.git -b v2.1.3.RELEASE
WORKDIR /spring-boot/spring-boot-samples/spring-boot-sample-web-static/
RUN mvn package

FROM java:latest
WORKDIR /
COPY --from=builder /spring-boot/spring-boot-samples/spring-boot-sample-web-static/target/spring-boot-sample-web-static-2.1.3.RELEASE.war web-static.war
EXPOSE 8080
CMD java -jar web-static.war
