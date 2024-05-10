#Gradle - base image
FROM gradle:6.0.1-jdk8 as builder

#Working directory -- into container
WORKDIR /app

# Coping gradle file
COPY build.gradle settings.gradle ./

# copy source code
COPY src ./src

# Build the application
RUN gradle installDist


FROM alpine:latest

# Installing OpenJDK
RUN apk add --no-cache openjdk8-jre

# Set the worki directory -- into container
WORKDIR /app

# Copy the app
COPY --from=builder /app/build/install/charts ./charts

# Set the entry point.
ENTRYPOINT ["/app/charts/bin/charts"]

