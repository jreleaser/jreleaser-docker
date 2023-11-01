# Generated with JReleaser 1.9.0-SNAPSHOT at 2023-11-01T11:30:46.9951+01:00
FROM alpine:latest

LABEL "org.opencontainers.image.title"="jreleaser-alpine"
LABEL "org.opencontainers.image.description"="Release projects quickly and easily with JReleaser"
LABEL "org.opencontainers.image.url"="https://jreleaser.org"
LABEL "org.opencontainers.image.licenses"="Apache-2.0"
LABEL "org.opencontainers.image.version"="1.9.0"
LABEL "org.opencontainers.image.revision"="383c727cc2ef91f8f54d4d5f2c9bc52c7e3bfa21"

RUN apk add unzip binutils fakeroot rpm bash

COPY assembly/* /

RUN unzip jreleaser-standalone-1.9.0-linux_musl-x86_64.zip && \
    rm jreleaser-standalone-1.9.0-linux_musl-x86_64.zip && \
    chmod +x jreleaser-standalone-1.9.0-linux_musl-x86_64/bin/jreleaser && \
    chmod +x jreleaser-standalone-1.9.0-linux_musl-x86_64/bin/java && \
    mv /jreleaser-entrypoint.sh /jreleaser-standalone-1.9.0-linux_musl-x86_64/bin && \
    chmod +x /jreleaser-standalone-1.9.0-linux_musl-x86_64/bin/jreleaser-entrypoint.sh && \
    mv /jreleaser-standalone-1.9.0-linux_musl-x86_64 /jreleaser

ENV PATH="${PATH}:/jreleaser/bin"

VOLUME /workspace

ENTRYPOINT ["/jreleaser/bin/jreleaser-entrypoint.sh"]
CMD ["/jreleaser/bin/jreleaser"]
