FROM maven:latest AS builder

RUN git clone https://github.com/spring-projects/spring-boot.git -b v2.1.3.RELEASE
WORKDIR /spring-boot/spring-boot-samples/spring-boot-sample-web-ui/
RUN mvn package

FROM java:latest
WORKDIR /
COPY --from=builder /spring-boot/spring-boot-samples/spring-boot-sample-web-ui/target/spring-boot-sample-web-ui-2.1.3.RELEASE.jar web-ui.jar
EXPOSE 8080
CMD java -jar web-ui.jar --server.servlet.context-path=/ui
