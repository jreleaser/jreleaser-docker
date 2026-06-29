# Generated with JReleaser 1.25.0-SNAPSHOT at 2026-06-29T07:57:31.988946286Z
# Multi-stage build to avoid duplicate layers

FROM alpine:latest AS extractor

RUN apk add --no-cache unzip

COPY assembly/ /assembly/

RUN unzip /assembly/jreleaser-standalone-1.25.0-linux-x86_64.zip -d /opt && \
    rm /assembly/jreleaser-standalone-1.25.0-linux-x86_64.zip && \
    chmod +x /opt/jreleaser-standalone-1.25.0-linux-x86_64/bin/jreleaser && \
    chmod +x /opt/jreleaser-standalone-1.25.0-linux-x86_64/bin/java

FROM registry.access.redhat.com/ubi10/ubi:latest

LABEL "org.opencontainers.image.title"="jreleaser-jreleaser-ubi"
LABEL "org.opencontainers.image.description"="Release projects quickly and easily with JReleaser"
LABEL "org.opencontainers.image.url"="https://jreleaser.org"
LABEL "org.opencontainers.image.licenses"="Apache-2.0"
LABEL "org.opencontainers.image.version"="1.25.0"
LABEL "org.opencontainers.image.revision"="76e2acc3a33b9e72f8c168799f27bb753bd54e6c"
LABEL "org.opencontainers.image.source"="https://github.com/jreleaser/jreleaser-docker"

ENV TZ=Europe/Zurich
RUN dnf update -y && dnf install -y unzip git && dnf clean all && rm -rf /var/cache/dnf /var/cache/microdnf

COPY --from=extractor /assembly /
COPY --from=extractor /opt/jreleaser-standalone-1.25.0-linux-x86_64 /jreleaser

VOLUME /workspace

ENV JAVA_HOME="/jreleaser"
ENV PATH="${PATH}:${JAVA_HOME}/bin"

ENTRYPOINT ["/jreleaser-entrypoint.sh"]
