# Generated with JReleaser 1.17.0-SNAPSHOT at 2025-01-02T15:49:42.991053914Z
FROM alpine:latest

LABEL "org.opencontainers.image.title"="jreleaser-alpine"
LABEL "org.opencontainers.image.description"="Release projects quickly and easily with JReleaser"
LABEL "org.opencontainers.image.url"="https://jreleaser.org"
LABEL "org.opencontainers.image.licenses"="Apache-2.0"
LABEL "org.opencontainers.image.version"="1.17.0-SNAPSHOT"
LABEL "org.opencontainers.image.revision"="9c09903c04d908c7d7e526a109911e0630e1f946"

RUN apk add unzip binutils fakeroot rpm bash

COPY assembly/* /

RUN unzip jreleaser-standalone-early-access-linux_musl-x86_64.zip && \
    rm jreleaser-standalone-early-access-linux_musl-x86_64.zip && \
    chmod +x jreleaser-standalone-early-access-linux_musl-x86_64/bin/jreleaser && \
    chmod +x jreleaser-standalone-early-access-linux_musl-x86_64/bin/java && \
    mv /jreleaser-entrypoint.sh /jreleaser-standalone-early-access-linux_musl-x86_64/bin && \
    chmod +x /jreleaser-standalone-early-access-linux_musl-x86_64/bin/jreleaser-entrypoint.sh && \
    mv /jreleaser-standalone-early-access-linux_musl-x86_64 /jreleaser

ENV PATH="${PATH}:/jreleaser/bin"

VOLUME /workspace

ENTRYPOINT ["/jreleaser/bin/jreleaser-entrypoint.sh"]
CMD ["/jreleaser/bin/jreleaser"]
