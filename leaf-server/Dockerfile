FROM openjdk:8-jre-alpine

COPY target/leaf.jar /app.jar
ENV SERVER_PORT 8080
ENV JAVA_OPTS=""

#编码方式
ENV LANG C.UTF-8

RUN sed -i s/dl-cdn\.alpinelinux\.org/mirrors.aliyun.com/g /etc/apk/repositories \
     && apk update \
     && apk --no-cache add bash curl tzdata \
     && cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime && echo "Asia/Shanghai" > /etc/timezone

EXPOSE ${SERVER_PORT}

ENTRYPOINT [ "sh", "-c", "java $JAVA_OPTS -Djava.security.egd=file:/dev/./urandom -jar /app.jar 2>&1" ]
