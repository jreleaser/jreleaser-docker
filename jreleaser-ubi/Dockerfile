# Generated with JReleaser 1.23.0-SNAPSHOT at 2026-01-27T10:14:11.859504701Z
FROM registry.access.redhat.com/ubi10/ubi:latest

LABEL "org.opencontainers.image.title"="jreleaser-jreleaser-ubi"
LABEL "org.opencontainers.image.description"="Release projects quickly and easily with JReleaser"
LABEL "org.opencontainers.image.url"="https://jreleaser.org"
LABEL "org.opencontainers.image.licenses"="Apache-2.0"
LABEL "org.opencontainers.image.version"="1.23.0-SNAPSHOT"
LABEL "org.opencontainers.image.revision"="df5a71c3fd9c6eb666ffe3a410cfab9e748d5b7b"
LABEL "org.opencontainers.image.source"="https://github.com/jreleaser/jreleaser-docker"

ENV TZ=Europe/Zurich
RUN dnf update -y && dnf install -y unzip git && dnf clean all && rm -rf /var/cache/dnf /var/cache/microdnf

COPY assembly/* /

RUN unzip jreleaser-standalone-early-access-linux-x86_64.zip && \
    rm jreleaser-standalone-early-access-linux-x86_64.zip && \
    chmod +x jreleaser-standalone-early-access-linux-x86_64/bin/jreleaser && \
    chmod +x jreleaser-standalone-early-access-linux-x86_64/bin/java && \
    mv /jreleaser-entrypoint.sh /jreleaser-standalone-early-access-linux-x86_64/bin && \
    chmod +x /jreleaser-standalone-early-access-linux-x86_64/bin/jreleaser-entrypoint.sh && \
    mv /jreleaser-standalone-early-access-linux-x86_64 /jreleaser

ENV PATH="${PATH}:/jreleaser/bin"

VOLUME /workspace

ENTRYPOINT ["/jreleaser/bin/jreleaser-entrypoint.sh"]
