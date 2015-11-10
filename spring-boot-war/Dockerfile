FROM bankmonitor/spring-boot

ONBUILD COPY app.war /app/app.war

CMD ["/bin/sh", "-c", "java -DCUSTOM_LOCAL_NAME=$CUSTOM_LOCAL_NAME -jar /app/app.war --spring.profiles.active=$SPRING_PROFILES_ACTIVE"]