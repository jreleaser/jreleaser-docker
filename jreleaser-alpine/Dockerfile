# Generated with JReleaser 1.12.0-SNAPSHOT at 2024-05-01T13:00:50.646676518Z
FROM alpine:latest

LABEL "org.opencontainers.image.title"="jreleaser-alpine"
LABEL "org.opencontainers.image.description"="Release projects quickly and easily with JReleaser"
LABEL "org.opencontainers.image.url"="https://jreleaser.org"
LABEL "org.opencontainers.image.licenses"="Apache-2.0"
LABEL "org.opencontainers.image.version"="1.12.0"
LABEL "org.opencontainers.image.revision"="8f5795140149238b358a64e43fa5b8f83e55f64d"

RUN apk add unzip binutils fakeroot rpm bash

COPY assembly/* /

RUN unzip jreleaser-standalone-1.12.0-linux_musl-x86_64.zip && \
    rm jreleaser-standalone-1.12.0-linux_musl-x86_64.zip && \
    chmod +x jreleaser-standalone-1.12.0-linux_musl-x86_64/bin/jreleaser && \
    chmod +x jreleaser-standalone-1.12.0-linux_musl-x86_64/bin/java && \
    mv /jreleaser-entrypoint.sh /jreleaser-standalone-1.12.0-linux_musl-x86_64/bin && \
    chmod +x /jreleaser-standalone-1.12.0-linux_musl-x86_64/bin/jreleaser-entrypoint.sh && \
    mv /jreleaser-standalone-1.12.0-linux_musl-x86_64 /jreleaser

ENV PATH="${PATH}:/jreleaser/bin"

VOLUME /workspace

ENTRYPOINT ["/jreleaser/bin/jreleaser-entrypoint.sh"]
CMD ["/jreleaser/bin/jreleaser"]
