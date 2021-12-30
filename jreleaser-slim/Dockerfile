FROM ubuntu:latest

LABEL "org.opencontainers.image.title"="jreleaser-slim"
LABEL "org.opencontainers.image.description"="Release projects quickly and easily with JReleaser"
LABEL "org.opencontainers.image.url"="https://jreleaser.org"
LABEL "org.opencontainers.image.licenses"="Apache-2.0"
LABEL "org.opencontainers.image.version"="1.0.0-SNAPSHOT"
LABEL "org.opencontainers.image.revision"="1b2aa2470db84acf83402b349c5cb46f04b9a3c0"

RUN apt-get update -y
RUN apt-get install unzip

COPY assembly/* /

RUN unzip jreleaser-standalone-early-access-linux-x86_64.zip && \
    rm jreleaser-standalone-early-access-linux-x86_64.zip && \
    chmod +x jreleaser-standalone-early-access-linux-x86_64/bin/jreleaser && \
    chmod +x jreleaser-standalone-early-access-linux-x86_64/bin/java && \
    mv /jreleaser-entrypoint.sh /jreleaser-standalone-early-access-linux-x86_64/bin && \
    chmod +x /jreleaser-standalone-early-access-linux-x86_64/bin/jreleaser-entrypoint.sh

ENV PATH="${PATH}:/jreleaser-standalone-early-access-linux-x86_64/bin"

VOLUME /workspace

ENTRYPOINT ["/jreleaser-standalone-early-access-linux-x86_64/bin/jreleaser-entrypoint.sh"]
CMD ["/jreleaser-standalone-early-access-linux-x86_64/bin/jreleaser"]
