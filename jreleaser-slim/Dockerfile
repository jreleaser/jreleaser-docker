# Generated with JReleaser 1.23.0-SNAPSHOT at 2026-02-28T07:45:23.249774677Z
FROM ubuntu:latest

LABEL "org.opencontainers.image.title"="jreleaser-jreleaser-slim"
LABEL "org.opencontainers.image.description"="Release projects quickly and easily with JReleaser"
LABEL "org.opencontainers.image.url"="https://jreleaser.org"
LABEL "org.opencontainers.image.licenses"="Apache-2.0"
LABEL "org.opencontainers.image.version"="1.23.0"
LABEL "org.opencontainers.image.revision"="d2a36952d63732f01faa52d764ebe4e067603ea9"
LABEL "org.opencontainers.image.source"="https://github.com/jreleaser/jreleaser-docker"

ARG DEBIAN_FRONTEND=noninteractive
ENV TZ=Europe/Zurich
RUN apt-get update && apt-get install -y unzip binutils fakeroot rpm git

COPY assembly/* /

RUN unzip jreleaser-standalone-1.23.0-linux-x86_64.zip && \
    rm jreleaser-standalone-1.23.0-linux-x86_64.zip && \
    chmod +x jreleaser-standalone-1.23.0-linux-x86_64/bin/jreleaser && \
    chmod +x jreleaser-standalone-1.23.0-linux-x86_64/bin/java && \
    mv /jreleaser-entrypoint.sh /jreleaser-standalone-1.23.0-linux-x86_64/bin && \
    chmod +x /jreleaser-standalone-1.23.0-linux-x86_64/bin/jreleaser-entrypoint.sh && \
    mv /jreleaser-standalone-1.23.0-linux-x86_64 /jreleaser

ENV PATH="${PATH}:/jreleaser/bin"

VOLUME /workspace

ENTRYPOINT ["/jreleaser/bin/jreleaser-entrypoint.sh"]
