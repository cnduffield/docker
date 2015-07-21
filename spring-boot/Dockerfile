FROM java:openjdk-8
MAINTAINER Földházi István <istvan.foldhazi@gmail.com>

ENV APPLICATION_NAME app
ENV SPRING_PROFILES_ACTIVE test

WORKDIR /app

COPY $APPLICATION_NAME.jar /app/$APPLICATION_NAME.jar

COPY start.sh /app/start.sh
RUN chmod +x /app/start.sh

EXPOSE 80

ENTRYPOINT /app/start.sh