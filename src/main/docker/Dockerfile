#FROM frolvlad/alpine-oraclejdk8:slim
FROM java:8
VOLUME /tmp
# Add repository for openssh to be added in the container
#RUN  apk add --no-cache  --repository http://dl-cdn.alpinelinux.org/alpine/edge/main --repository  http://dl-cdn.alpinelinux.org/alpine/edge/community  docker
#add openssh for container
#RUN apk --update add openssh  
#generate public key
RUN ssh-keygen -t rsa -f /root/.ssh/id_rsa -q -P "testtest"
#add bitbucket in known_hosts
RUN ssh-keyscan -t rsa -p 80  bitbucket.org >> ~/.ssh/known_hosts
ADD configuration-client-0.0.1-SNAPSHOT.jar app.jar
RUN sh -c 'touch /app.jar'
ENV JAVA_OPTS=""
ENTRYPOINT [ "sh", "-c", "java $JAVA_OPTS -Djava.security.egd=file:/dev/./urandom -jar /app.jar" ]
