# Generated with JReleaser 1.21.0-SNAPSHOT at 2025-10-31T09:02:17.092272113Z
FROM alpine:latest

LABEL "org.opencontainers.image.title"="jreleaser-jreleaser-alpine"
LABEL "org.opencontainers.image.description"="Release projects quickly and easily with JReleaser"
LABEL "org.opencontainers.image.url"="https://jreleaser.org"
LABEL "org.opencontainers.image.licenses"="Apache-2.0"
LABEL "org.opencontainers.image.version"="1.21.0"
LABEL "org.opencontainers.image.revision"="6292b2514bd58b59b91433f2981226da0912acd9"
LABEL "org.opencontainers.image.source"="https://github.com/jreleaser/jreleaser-docker"

RUN apk add unzip binutils fakeroot rpm bash git

COPY assembly/ /

RUN unzip jreleaser-standalone-1.21.0-linux_musl-x86_64.zip && \
    rm jreleaser-standalone-1.21.0-linux_musl-x86_64.zip && \
    chmod +x jreleaser-standalone-1.21.0-linux_musl-x86_64/bin/jreleaser && \
    chmod +x jreleaser-standalone-1.21.0-linux_musl-x86_64/bin/java

VOLUME /workspace

ENV JAVA_HOME="/jreleaser-standalone-1.21.0-linux_musl-x86_64"
ENV PATH="${PATH}:${JAVA_HOME}/bin"

ENTRYPOINT ["/jreleaser-standalone-1.21.0-linux_musl-x86_64/bin/jreleaser"]
