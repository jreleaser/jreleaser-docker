# Generated with JReleaser 1.0.0-SNAPSHOT at 2022-02-13T12:11:01.494659Z
FROM ubuntu:latest

LABEL "org.opencontainers.image.title"="jreleaser-slim"
LABEL "org.opencontainers.image.description"="Release projects quickly and easily with JReleaser"
LABEL "org.opencontainers.image.url"="https://jreleaser.org"
LABEL "org.opencontainers.image.licenses"="Apache-2.0"
LABEL "org.opencontainers.image.version"="1.0.0-M2"
LABEL "org.opencontainers.image.revision"="7644e02b12bfa7f9105727b928583086e894950f"

RUN apt-get update -y
RUN apt-get install unzip

COPY assembly/* /

RUN unzip jreleaser-standalone-1.0.0-M2-linux-x86_64.zip && \
    rm jreleaser-standalone-1.0.0-M2-linux-x86_64.zip && \
    chmod +x jreleaser-standalone-1.0.0-M2-linux-x86_64/bin/jreleaser && \
    chmod +x jreleaser-standalone-1.0.0-M2-linux-x86_64/bin/java && \
    mv /jreleaser-entrypoint.sh /jreleaser-standalone-1.0.0-M2-linux-x86_64/bin && \
    chmod +x /jreleaser-standalone-1.0.0-M2-linux-x86_64/bin/jreleaser-entrypoint.sh

ENV PATH="${PATH}:/jreleaser-standalone-1.0.0-M2-linux-x86_64/bin"

VOLUME /workspace

ENTRYPOINT ["/jreleaser-standalone-1.0.0-M2-linux-x86_64/bin/jreleaser-entrypoint.sh"]
CMD ["/jreleaser-standalone-1.0.0-M2-linux-x86_64/bin/jreleaser"]
