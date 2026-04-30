# Generated with JReleaser 1.24.0-SNAPSHOT at 2026-04-30T11:17:23.903587413Z
# Multi-stage build to avoid duplicate layers

FROM alpine:latest AS extractor

RUN apk add --no-cache unzip

COPY assembly/ /assembly/

RUN unzip /assembly/jreleaser-standalone-1.24.0-linux_musl-x86_64.zip -d /opt && \
    rm /assembly/jreleaser-standalone-1.24.0-linux_musl-x86_64.zip && \
    chmod +x /opt/jreleaser-standalone-1.24.0-linux_musl-x86_64/bin/jreleaser && \
    chmod +x /opt/jreleaser-standalone-1.24.0-linux_musl-x86_64/bin/java

FROM alpine:latest

LABEL "org.opencontainers.image.title"="jreleaser-jreleaser-alpine"
LABEL "org.opencontainers.image.description"="Release projects quickly and easily with JReleaser"
LABEL "org.opencontainers.image.url"="https://jreleaser.org"
LABEL "org.opencontainers.image.licenses"="Apache-2.0"
LABEL "org.opencontainers.image.version"="1.24.0"
LABEL "org.opencontainers.image.revision"="4def7226a85e911d0a103b40a1857fb191aada0d"
LABEL "org.opencontainers.image.source"="https://github.com/jreleaser/jreleaser-docker"

RUN apk add unzip binutils fakeroot rpm bash git

COPY --from=extractor /assembly /
COPY --from=extractor /opt/jreleaser-standalone-1.24.0-linux_musl-x86_64 /jreleaser

VOLUME /workspace

ENV JAVA_HOME="/jreleaser"
ENV PATH="${PATH}:${JAVA_HOME}/bin"

ENTRYPOINT ["/jreleaser-entrypoint.sh"]
