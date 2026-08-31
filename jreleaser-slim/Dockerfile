# Generated with JReleaser 1.26.0-SNAPSHOT at 2026-08-31T07:37:41.529332195Z
# Multi-stage build to avoid duplicate layers

FROM alpine:latest AS extractor

RUN apk add --no-cache unzip

COPY assembly/ /assembly/

RUN unzip /assembly/jreleaser-standalone-1.26.0-linux-x86_64.zip -d /opt && \
    rm /assembly/jreleaser-standalone-1.26.0-linux-x86_64.zip && \
    chmod +x /opt/jreleaser-standalone-1.26.0-linux-x86_64/bin/jreleaser && \
    chmod +x /opt/jreleaser-standalone-1.26.0-linux-x86_64/bin/java

FROM ubuntu:latest

LABEL "org.opencontainers.image.title"="jreleaser-jreleaser-slim"
LABEL "org.opencontainers.image.description"="Release projects quickly and easily with JReleaser"
LABEL "org.opencontainers.image.url"="https://jreleaser.org"
LABEL "org.opencontainers.image.licenses"="Apache-2.0"
LABEL "org.opencontainers.image.version"="1.26.0"
LABEL "org.opencontainers.image.revision"="8fb9ed6642e1c73a133d2bae96ea8e35df919bd5"
LABEL "org.opencontainers.image.source"="https://github.com/jreleaser/jreleaser-docker"

ARG DEBIAN_FRONTEND=noninteractive
ENV TZ=Europe/Zurich
RUN apt-get update && apt-get install -y unzip binutils fakeroot rpm git

COPY --from=extractor /assembly /
COPY --from=extractor /opt/jreleaser-standalone-1.26.0-linux-x86_64 /jreleaser

VOLUME /workspace

ENV JAVA_HOME="/jreleaser"
ENV PATH="${PATH}:${JAVA_HOME}/bin"

ENTRYPOINT ["/jreleaser-entrypoint.sh"]
