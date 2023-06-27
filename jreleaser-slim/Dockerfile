# Generated with JReleaser 1.7.0-SNAPSHOT at 2023-06-27T13:02:28.955362088Z
FROM ubuntu:latest

LABEL "org.opencontainers.image.title"="jreleaser-slim"
LABEL "org.opencontainers.image.description"="Release projects quickly and easily with JReleaser"
LABEL "org.opencontainers.image.url"="https://jreleaser.org"
LABEL "org.opencontainers.image.licenses"="Apache-2.0"
LABEL "org.opencontainers.image.version"="1.7.0"
LABEL "org.opencontainers.image.revision"="5774c3f318e7db1c896e592b7ca8634e1da44832"

ARG DEBIAN_FRONTEND=noninteractive
ENV TZ=Europe/Zurich
RUN apt-get update && apt-get install -y unzip binutils fakeroot rpm

COPY assembly/* /

RUN unzip jreleaser-standalone-1.7.0-linux-x86_64.zip && \
    rm jreleaser-standalone-1.7.0-linux-x86_64.zip && \
    chmod +x jreleaser-standalone-1.7.0-linux-x86_64/bin/jreleaser && \
    chmod +x jreleaser-standalone-1.7.0-linux-x86_64/bin/java && \
    mv /jreleaser-entrypoint.sh /jreleaser-standalone-1.7.0-linux-x86_64/bin && \
    chmod +x /jreleaser-standalone-1.7.0-linux-x86_64/bin/jreleaser-entrypoint.sh && \
    mv /jreleaser-standalone-1.7.0-linux-x86_64 /jreleaser

ENV PATH="${PATH}:/jreleaser/bin"

VOLUME /workspace

ENTRYPOINT ["/jreleaser/bin/jreleaser-entrypoint.sh"]
CMD ["/jreleaser/bin/jreleaser"]
