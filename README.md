# Spring Boot image

[![](https://img.shields.io/docker/stars/bankmonitor/spring-boot.svg)](https://hub.docker.com/r/bankmonitor/spring-boot/ 'Docker hub')
[![](https://img.shields.io/docker/pulls/bankmonitor/spring-boot.svg)](https://hub.docker.com/r/bankmonitor/spring-boot/ 'Docker hub')
[![](https://badge.imagelayers.io/bankmonitor/spring-boot:latest.svg)](https://imagelayers.io/?images=bankmonitor/spring-boot:latest 'Get your own badge on imagelayers.io')

Version: 0.4

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

## Testing the image (step-by-step)


* Step 1: Create a new folder

```bash
mkdir my-docker-test
cd my-docker-test
```

* Step 2: Build the sample app

You could test the image with our sample app: [sample-app](https://github.com/Bankmonitor/sample-app)

```bash
git clone https://github.com/Bankmonitor/sample-app.git /tmp/sample-app
mvn -f /tmp/sample-app/pom.xml clean package
cp /tmp/sample-app/target/app.jar app.jar
```

* Step 3: Create a new `Dockerfile`

Dockerfile contents:

```Dockerfile
FROM bankmonitor:spring-boot:latest-jar
```

* Step 4: Build the new image

```bash
docker build --tag=sample-app .
```

* Step 5: Run the new image

```bash
docker run -p 8080:8080 sample-app
```

* Step 6: Test the app is started

The following command should return 'OK':

```bash
curl http://localhost:8080/status
```
