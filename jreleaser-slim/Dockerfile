# Generated with JReleaser 1.1.0-SNAPSHOT at 2022-06-30T15:46:43.841258289Z
FROM ubuntu:latest

LABEL "org.opencontainers.image.title"="jreleaser-slim"
LABEL "org.opencontainers.image.description"="Release projects quickly and easily with JReleaser"
LABEL "org.opencontainers.image.url"="https://jreleaser.org"
LABEL "org.opencontainers.image.licenses"="Apache-2.0"
LABEL "org.opencontainers.image.version"="1.1.0"
LABEL "org.opencontainers.image.revision"="a8fe179f3750da37006173595825317188d5b486"

ARG DEBIAN_FRONTEND=noninteractive
ENV TZ=Europe/Zurich
RUN apt-get update && apt-get install -y unzip binutils fakeroot rpm

COPY assembly/* /

RUN unzip jreleaser-standalone-1.1.0-linux-x86_64.zip && \
    rm jreleaser-standalone-1.1.0-linux-x86_64.zip && \
    chmod +x jreleaser-standalone-1.1.0-linux-x86_64/bin/jreleaser && \
    chmod +x jreleaser-standalone-1.1.0-linux-x86_64/bin/java && \
    mv /jreleaser-entrypoint.sh /jreleaser-standalone-1.1.0-linux-x86_64/bin && \
    chmod +x /jreleaser-standalone-1.1.0-linux-x86_64/bin/jreleaser-entrypoint.sh

ENV PATH="${PATH}:/jreleaser-standalone-1.1.0-linux-x86_64/bin"

VOLUME /workspace

ENTRYPOINT ["/jreleaser-standalone-1.1.0-linux-x86_64/bin/jreleaser-entrypoint.sh"]
CMD ["/jreleaser-standalone-1.1.0-linux-x86_64/bin/jreleaser"]
