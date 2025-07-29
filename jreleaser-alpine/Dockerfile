# Generated with JReleaser 1.20.0-SNAPSHOT at 2025-07-29T22:03:21.594229998Z
FROM alpine:latest

LABEL "org.opencontainers.image.title"="jreleaser-jreleaser-alpine"
LABEL "org.opencontainers.image.description"="Release projects quickly and easily with JReleaser"
LABEL "org.opencontainers.image.url"="https://jreleaser.org"
LABEL "org.opencontainers.image.licenses"="Apache-2.0"
LABEL "org.opencontainers.image.version"="1.20.0-SNAPSHOT"
LABEL "org.opencontainers.image.revision"="3046d3a909fb93dbece298f83f228151eecf786a"
LABEL "org.opencontainers.image.source"="https://github.com/jreleaser/jreleaser-docker"

RUN apk add unzip binutils fakeroot rpm bash git

COPY assembly/ /

RUN unzip jreleaser-standalone-early-access-linux_musl-x86_64.zip && \
    rm jreleaser-standalone-early-access-linux_musl-x86_64.zip && \
    chmod +x jreleaser-standalone-early-access-linux_musl-x86_64/bin/jreleaser && \
    chmod +x jreleaser-standalone-early-access-linux_musl-x86_64/bin/java

VOLUME /workspace

ENV JAVA_HOME="/jreleaser-standalone-early-access-linux_musl-x86_64"
ENV PATH="${PATH}:${JAVA_HOME}/bin"

ENTRYPOINT ["/jreleaser-standalone-early-access-linux_musl-x86_64/bin/jreleaser"]
