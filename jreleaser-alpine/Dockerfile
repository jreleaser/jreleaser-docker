# Generated with JReleaser 1.0.0-SNAPSHOT at 2022-01-22T09:46:39.196814Z
FROM alpine:latest

LABEL "org.opencontainers.image.title"="jreleaser-alpine"
LABEL "org.opencontainers.image.description"="Release projects quickly and easily with JReleaser"
LABEL "org.opencontainers.image.url"="https://jreleaser.org"
LABEL "org.opencontainers.image.licenses"="Apache-2.0"
LABEL "org.opencontainers.image.version"="1.0.0-M1"
LABEL "org.opencontainers.image.revision"="2489915b925abc10a1f0c4cf2afa2fae75f031ba"

RUN apk add unzip

COPY assembly/* /

RUN unzip jreleaser-standalone-1.0.0-M1-linux_musl-x86_64.zip && \
    rm jreleaser-standalone-1.0.0-M1-linux_musl-x86_64.zip && \
    chmod +x jreleaser-standalone-1.0.0-M1-linux_musl-x86_64/bin/jreleaser && \
    chmod +x jreleaser-standalone-1.0.0-M1-linux_musl-x86_64/bin/java && \
    mv /jreleaser-entrypoint.sh /jreleaser-standalone-1.0.0-M1-linux_musl-x86_64/bin && \
    chmod +x /jreleaser-standalone-1.0.0-M1-linux_musl-x86_64/bin/jreleaser-entrypoint.sh

ENV PATH="${PATH}:/jreleaser-standalone-1.0.0-M1-linux_musl-x86_64/bin"

VOLUME /workspace

ENTRYPOINT ["/jreleaser-standalone-1.0.0-M1-linux_musl-x86_64/bin/jreleaser-entrypoint.sh"]
CMD ["/jreleaser-standalone-1.0.0-M1-linux_musl-x86_64/bin/jreleaser"]
