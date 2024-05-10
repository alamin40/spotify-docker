#Gradle base image
FROM gradle:6.0.1-jdk8 as builder

#Working directory -- into container
WORKDIR /app

#Copy Gradle build files
COPY build.gradle settings.gradle ./

#Copy full source code
COPY src ./src

#Build the app
RUN gradle installDist


FROM alpine:latest

#Install OpenJDK
RUN apk add --no-cache openjdk8-jre

#Working directory -- into container
WORKDIR /app

#copy compiled appl artifacts
COPY --from=builder /app/build/install/images ./images

#set enty point
ENTRYPOINT ["/app/images/bin/images"]

