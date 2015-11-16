FROM java:8-jdk
MAINTAINER István Földházi <istvan.foldhazi@gmail.com>

ENV JAVA_HOME              /usr/lib/jvm/java-8-openjdk-amd64
ENV PATH                   $PATH:$JAVA_HOME/bin

ENV TIME_ZONE              Europe/Budapest
ENV CUSTOM_LOCAL_NAME      unknown-host
ENV SPRING_PROFILES_ACTIVE test

RUN apt-get update && apt-get install -y \
    curl \
    && rm -rf /var/lib/apt/lists/*

RUN echo "$TIME_ZONE" > /etc/timezone
RUN dpkg-reconfigure -f noninteractive tzdata

WORKDIR /app

EXPOSE 8080

ONBUILD COPY app.war /app/app.war

CMD ["/bin/sh", "-c", "java -DCUSTOM_LOCAL_NAME=$CUSTOM_LOCAL_NAME -jar /app/app.war --spring.profiles.active=$SPRING_PROFILES_ACTIVE"]