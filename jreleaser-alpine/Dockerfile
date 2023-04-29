# Generated with JReleaser 1.6.0-SNAPSHOT at 2023-04-29T10:13:03.544759325Z
FROM alpine:latest

LABEL "org.opencontainers.image.title"="jreleaser-alpine"
LABEL "org.opencontainers.image.description"="Release projects quickly and easily with JReleaser"
LABEL "org.opencontainers.image.url"="https://jreleaser.org"
LABEL "org.opencontainers.image.licenses"="Apache-2.0"
LABEL "org.opencontainers.image.version"="1.6.0"
LABEL "org.opencontainers.image.revision"="fccb6ee7cbf897dc19a0cceffd06db7f3b7ef708"

RUN apk add unzip binutils fakeroot rpm bash

COPY assembly/* /

RUN unzip jreleaser-standalone-1.6.0-linux_musl-x86_64.zip && \
    rm jreleaser-standalone-1.6.0-linux_musl-x86_64.zip && \
    chmod +x jreleaser-standalone-1.6.0-linux_musl-x86_64/bin/jreleaser && \
    chmod +x jreleaser-standalone-1.6.0-linux_musl-x86_64/bin/java && \
    mv /jreleaser-entrypoint.sh /jreleaser-standalone-1.6.0-linux_musl-x86_64/bin && \
    chmod +x /jreleaser-standalone-1.6.0-linux_musl-x86_64/bin/jreleaser-entrypoint.sh && \
    mv /jreleaser-standalone-1.6.0-linux_musl-x86_64 /jreleaser

ENV PATH="${PATH}:/jreleaser/bin"

VOLUME /workspace

ENTRYPOINT ["/jreleaser/bin/jreleaser-entrypoint.sh"]
CMD ["/jreleaser/bin/jreleaser"]
