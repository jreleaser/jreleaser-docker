# Generated with JReleaser 1.0.0-SNAPSHOT at 2022-01-09T18:05:41.832843Z
FROM alpine:latest

LABEL "org.opencontainers.image.title"="jreleaser-alpine"
LABEL "org.opencontainers.image.description"="Release projects quickly and easily with JReleaser"
LABEL "org.opencontainers.image.url"="https://jreleaser.org"
LABEL "org.opencontainers.image.licenses"="Apache-2.0"
LABEL "org.opencontainers.image.version"="1.0.0-SNAPSHOT"
LABEL "org.opencontainers.image.revision"="5b78c357481aa7b96b568b6b726ba97d04224f5e"

RUN apk add unzip

COPY assembly/* /

RUN unzip jreleaser-standalone-early-access-linux_musl-x86_64.zip && \
    rm jreleaser-standalone-early-access-linux_musl-x86_64.zip && \
    chmod +x jreleaser-standalone-early-access-linux_musl-x86_64/bin/jreleaser && \
    chmod +x jreleaser-standalone-early-access-linux_musl-x86_64/bin/java && \
    mv /jreleaser-entrypoint.sh /jreleaser-standalone-early-access-linux_musl-x86_64/bin && \
    chmod +x /jreleaser-standalone-early-access-linux_musl-x86_64/bin/jreleaser-entrypoint.sh

ENV PATH="${PATH}:/jreleaser-standalone-early-access-linux_musl-x86_64/bin"

VOLUME /workspace

ENTRYPOINT ["/jreleaser-standalone-early-access-linux_musl-x86_64/bin/jreleaser-entrypoint.sh"]
CMD ["/jreleaser-standalone-early-access-linux_musl-x86_64/bin/jreleaser"]
