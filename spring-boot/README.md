# Spring Boot image


## Environment variables

Name                    | Default                 | Description
------------------------|-------------------------|------------------------------------
TIME_ZONE               | 'Europe/Budapest'       | The time zone [(List of tz database time zones)](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones)
CUSTOM_LOCAL_NAME       | 'unknown-host'          | A custom local name used in our custom Logback Syslog4j appender [(BankmonitorSyslogMessageProcessor)](https://github.com/Bankmonitor/microservice-starters/blob/0.0.44/microservice-starter-common/src/main/java/hu/bankmonitor/starter/microservice/common/log/BankmonitorSyslogMessageProcessor.java#L30)
APPLICATION_NAME        | 'app'                   | The application name
APPLICATION_FILE        | '$APPLICATION_NAME.jar' | The JAR/WAR file name to execute
SPRING_PROFILES_ACTIVE  | 'test'                  | Active Spring profiles
