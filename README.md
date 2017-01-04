# Spring Boot image

[![](https://img.shields.io/docker/stars/bankmonitor/spring-boot.svg)](https://hub.docker.com/r/bankmonitor/spring-boot/ 'Docker hub')
[![](https://img.shields.io/docker/pulls/bankmonitor/spring-boot.svg)](https://hub.docker.com/r/bankmonitor/spring-boot/ 'Docker hub')
[![](https://images.microbadger.com/badges/image/bankmonitor/spring-boot.svg)](https://microbadger.com/images/bankmonitor/spring-boot "Get your own image badge on microbadger.com")

Version: 1.0

We use the Dockerfiles in production but this repository is under heavy development and can change anytime.

## Docker Tags

- [`latest`](https://github.com/Bankmonitor/docker/blob/master/Dockerfile): image for JAR application
- [`latest-war`](https://github.com/Bankmonitor/docker/blob/war/Dockerfile): image for WAR application

## Environment variables

Name                    | Default                 | Description
------------------------|-------------------------|------------------------------------
JAVA_OPTS               | (empty)                 | Java command line options
TIME_ZONE               | 'Europe/Budapest'       | The time zone [(List of tz database time zones)](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones)
SPRING_PROFILES_ACTIVE  | 'test'                  | Active Spring profiles

## Testing the image (step-by-step)


* Step 1: Create a new folder

```bash
mkdir my-docker-test
cd my-docker-test
```

* Step 2: Build the sample app (Skip to step 3. This will be pulled down the the ADD command.)

You could test the image with our sample app: [sample-app](https://github.com/Bankmonitor/sample-app)

```bash
git clone https://github.com/Bankmonitor/sample-app.git /tmp/sample-app
mvn -f /tmp/sample-app/pom.xml clean package
cp /tmp/sample-app/target/app.jar app.jar
```

* Step 3: Create a new `Dockerfile`

Dockerfile contents:

```Dockerfile
FROM cnduffield/dockerspringtest
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
