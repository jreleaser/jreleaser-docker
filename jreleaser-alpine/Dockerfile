# Generated with JReleaser 1.0.0-SNAPSHOT at 2022-04-02T15:50:07.287489Z
FROM alpine:latest

LABEL "org.opencontainers.image.title"="jreleaser-alpine"
LABEL "org.opencontainers.image.description"="Release projects quickly and easily with JReleaser"
LABEL "org.opencontainers.image.url"="https://jreleaser.org"
LABEL "org.opencontainers.image.licenses"="Apache-2.0"
LABEL "org.opencontainers.image.version"="1.0.0-RC2"
LABEL "org.opencontainers.image.revision"="0cf4c03df06b9d2c33e788f082f87930ddec37ce"

RUN apk add unzip binutils fakeroot rpm

COPY assembly/* /

RUN unzip jreleaser-standalone-1.0.0-RC2-linux_musl-x86_64.zip && \
    rm jreleaser-standalone-1.0.0-RC2-linux_musl-x86_64.zip && \
    chmod +x jreleaser-standalone-1.0.0-RC2-linux_musl-x86_64/bin/jreleaser && \
    chmod +x jreleaser-standalone-1.0.0-RC2-linux_musl-x86_64/bin/java && \
    mv /jreleaser-entrypoint.sh /jreleaser-standalone-1.0.0-RC2-linux_musl-x86_64/bin && \
    chmod +x /jreleaser-standalone-1.0.0-RC2-linux_musl-x86_64/bin/jreleaser-entrypoint.sh

ENV PATH="${PATH}:/jreleaser-standalone-1.0.0-RC2-linux_musl-x86_64/bin"

VOLUME /workspace

ENTRYPOINT ["/jreleaser-standalone-1.0.0-RC2-linux_musl-x86_64/bin/jreleaser-entrypoint.sh"]
CMD ["/jreleaser-standalone-1.0.0-RC2-linux_musl-x86_64/bin/jreleaser"]
