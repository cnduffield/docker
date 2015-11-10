FROM bankmonitor/spring-boot

ONBUILD COPY app.jar /app/app.jar

CMD ["/bin/sh", "-c", "java -DCUSTOM_LOCAL_NAME=$CUSTOM_LOCAL_NAME -jar /app/app.jar --spring.profiles.active=$SPRING_PROFILES_ACTIVE"]