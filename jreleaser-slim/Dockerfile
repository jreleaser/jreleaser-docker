# Generated with JReleaser 1.17.0-SNAPSHOT at 2025-01-17T18:33:27.103956643Z
FROM ubuntu:latest

LABEL "org.opencontainers.image.title"="jreleaser-slim"
LABEL "org.opencontainers.image.description"="Release projects quickly and easily with JReleaser"
LABEL "org.opencontainers.image.url"="https://jreleaser.org"
LABEL "org.opencontainers.image.licenses"="Apache-2.0"
LABEL "org.opencontainers.image.version"="1.17.0-SNAPSHOT"
LABEL "org.opencontainers.image.revision"="de6f2337650bb513bd083e622c6fa7a31767f4a8"

ARG DEBIAN_FRONTEND=noninteractive
ENV TZ=Europe/Zurich
RUN apt-get update && apt-get install -y unzip binutils fakeroot rpm

COPY assembly/* /

RUN unzip jreleaser-standalone-early-access-linux-x86_64.zip && \
    rm jreleaser-standalone-early-access-linux-x86_64.zip && \
    chmod +x jreleaser-standalone-early-access-linux-x86_64/bin/jreleaser && \
    chmod +x jreleaser-standalone-early-access-linux-x86_64/bin/java && \
    mv /jreleaser-entrypoint.sh /jreleaser-standalone-early-access-linux-x86_64/bin && \
    chmod +x /jreleaser-standalone-early-access-linux-x86_64/bin/jreleaser-entrypoint.sh && \
    mv /jreleaser-standalone-early-access-linux-x86_64 /jreleaser

ENV PATH="${PATH}:/jreleaser/bin"

VOLUME /workspace

ENTRYPOINT ["/jreleaser/bin/jreleaser-entrypoint.sh"]
CMD ["/jreleaser/bin/jreleaser"]
