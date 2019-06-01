FROM openjdk:8-jre

MAINTAINER binzikeji <binzikeji@qq.com>

RUN wget https://github.com/jwilder/dockerize/releases/download/v0.6.1/dockerize-linux-amd64-v0.6.1.tar.gz \
    && tar -C /usr/local/bin -xzvf dockerize-linux-amd64-v0.6.1.tar.gz \
    && rm dockerize-linux-amd64-v0.6.1.tar.gz

RUN mkdir /app

COPY itoken-zipkin-1.0.0-SNAPSHOT.jar /app/app.jar
ENTRYPOINT ["dockerize", "-timeout", "5m", "-wait", "http://10.0.2.27:8888/itoken-zipkin/prod/master", "java", "-Djava.security.egd=file:/dev/./urandom", "-jar", "/app/app.jar", "--spring.profiles.active=prod"]

EXPOSE 9411