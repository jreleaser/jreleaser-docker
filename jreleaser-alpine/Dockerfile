# Generated with JReleaser 1.0.0-SNAPSHOT at 2022-03-05T15:54:17.031894Z
FROM alpine:latest

LABEL "org.opencontainers.image.title"="jreleaser-alpine"
LABEL "org.opencontainers.image.description"="Release projects quickly and easily with JReleaser"
LABEL "org.opencontainers.image.url"="https://jreleaser.org"
LABEL "org.opencontainers.image.licenses"="Apache-2.0"
LABEL "org.opencontainers.image.version"="1.0.0-M3"
LABEL "org.opencontainers.image.revision"="b6eee575b622ffacb5dadb33354c9ad457f71b0d"

RUN apk add unzip binutils fakeroot rpm

COPY assembly/* /

RUN unzip jreleaser-standalone-1.0.0-M3-linux_musl-x86_64.zip && \
    rm jreleaser-standalone-1.0.0-M3-linux_musl-x86_64.zip && \
    chmod +x jreleaser-standalone-1.0.0-M3-linux_musl-x86_64/bin/jreleaser && \
    chmod +x jreleaser-standalone-1.0.0-M3-linux_musl-x86_64/bin/java && \
    mv /jreleaser-entrypoint.sh /jreleaser-standalone-1.0.0-M3-linux_musl-x86_64/bin && \
    chmod +x /jreleaser-standalone-1.0.0-M3-linux_musl-x86_64/bin/jreleaser-entrypoint.sh

ENV PATH="${PATH}:/jreleaser-standalone-1.0.0-M3-linux_musl-x86_64/bin"

VOLUME /workspace

ENTRYPOINT ["/jreleaser-standalone-1.0.0-M3-linux_musl-x86_64/bin/jreleaser-entrypoint.sh"]
CMD ["/jreleaser-standalone-1.0.0-M3-linux_musl-x86_64/bin/jreleaser"]
