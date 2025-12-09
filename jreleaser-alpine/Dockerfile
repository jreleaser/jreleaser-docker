# Generated with JReleaser 1.22.0-SNAPSHOT at 2025-12-09T19:20:39.562961209Z
FROM alpine:latest

LABEL "org.opencontainers.image.title"="jreleaser-jreleaser-alpine"
LABEL "org.opencontainers.image.description"="Release projects quickly and easily with JReleaser"
LABEL "org.opencontainers.image.url"="https://jreleaser.org"
LABEL "org.opencontainers.image.licenses"="Apache-2.0"
LABEL "org.opencontainers.image.version"="1.22.0-SNAPSHOT"
LABEL "org.opencontainers.image.revision"="a5036e096af1b5d5281e4a31cea1f67c436a3889"
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
