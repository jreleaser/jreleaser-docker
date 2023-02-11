# Generated with JReleaser 1.5.0-SNAPSHOT at 2023-02-11T22:27:32.460341679Z
FROM alpine:latest

LABEL "org.opencontainers.image.title"="jreleaser-alpine"
LABEL "org.opencontainers.image.description"="Release projects quickly and easily with JReleaser"
LABEL "org.opencontainers.image.url"="https://jreleaser.org"
LABEL "org.opencontainers.image.licenses"="Apache-2.0"
LABEL "org.opencontainers.image.version"="1.5.0-SNAPSHOT"
LABEL "org.opencontainers.image.revision"="9c76ac4d8c467f89d531a9e4b65a41b3331eefb0"

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
