# Generated with JReleaser 1.21.0-SNAPSHOT at 2025-10-28T16:56:47.039218794Z
FROM ubuntu:latest

LABEL "org.opencontainers.image.title"="jreleaser-jreleaser-slim"
LABEL "org.opencontainers.image.description"="Release projects quickly and easily with JReleaser"
LABEL "org.opencontainers.image.url"="https://jreleaser.org"
LABEL "org.opencontainers.image.licenses"="Apache-2.0"
LABEL "org.opencontainers.image.version"="1.21.0-SNAPSHOT"
LABEL "org.opencontainers.image.revision"="6ffa24577fe392baf39ec29932370e4e37c9b178"
LABEL "org.opencontainers.image.source"="https://github.com/jreleaser/jreleaser-docker"

ARG DEBIAN_FRONTEND=noninteractive
ENV TZ=Europe/Zurich
RUN apt-get update && apt-get install -y unzip binutils fakeroot rpm git

COPY assembly/ /

RUN unzip jreleaser-standalone-early-access-linux-x86_64.zip && \
    rm jreleaser-standalone-early-access-linux-x86_64.zip && \
    chmod +x jreleaser-standalone-early-access-linux-x86_64/bin/jreleaser && \
    chmod +x jreleaser-standalone-early-access-linux-x86_64/bin/java

VOLUME /workspace

ENV JAVA_HOME="/jreleaser-standalone-early-access-linux-x86_64"
ENV PATH="${PATH}:${JAVA_HOME}/bin"

ENTRYPOINT ["/jreleaser-standalone-early-access-linux-x86_64/bin/jreleaser"]
