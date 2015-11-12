# Spring Boot image

Version: 0.2 (alpha)

We use the Dockerfiles in production but this repository is under heavy development and can change anytime.

## Tags

- [`latest`](https://github.com/Bankmonitor/docker/blob/master/spring-boot/Dockerfile): base image
- [`latest-jar`](https://github.com/Bankmonitor/docker/blob/master/spring-boot-jar/Dockerfile): image for JAR application
- [`latest-war`](https://github.com/Bankmonitor/docker/blob/master/spring-boot-jar/Dockerfile): image for WAR application

## Environment variables

Name                    | Default                 | Description
------------------------|-------------------------|------------------------------------
TIME_ZONE               | 'Europe/Budapest'       | The time zone [(List of tz database time zones)](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones)
CUSTOM_LOCAL_NAME       | 'unknown-host'          | A custom local name used in our custom Logback Syslog4j appender [(BankmonitorSyslogMessageProcessor)](https://github.com/Bankmonitor/microservice-starters/blob/0.0.44/microservice-starter-common/src/main/java/hu/bankmonitor/starter/microservice/common/log/BankmonitorSyslogMessageProcessor.java#L30)
SPRING_PROFILES_ACTIVE  | 'test'                  | Active Spring profiles

## Testing the image

You could test the image with our sample app: [sample-app](https://github.com/Bankmonitor/sample-app)

Create a Dockerfile:

```Dockerfile
FROM bankmonitor:spring-boot:latest-jar
```

```bash
docker build --tag=sample-app .
docker run -p 8080:8080 sample-app
curl http://localhost:8080/status
```
