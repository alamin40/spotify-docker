#Gradle base image
FROM gradle:6.0.1-jdk8 as builder

#Set work directory -- into container
WORKDIR /app

#Copy the Gradle build files
COPY build.gradle settings.gradle ./

#Copy the entire source code
COPY src ./src

# Build the app
RUN gradle installDist


FROM alpine:latest

#Install OpenJDK
RUN apk add --no-cache openjdk8-jre

#Set work directory -- into container
WORKDIR /app

#Copy compiled application artifacts
COPY --from=builder /app/build/install/search ./search

#Set entry point to start
ENTRYPOINT ["/app/search/bin/search"]

