# Generated with JReleaser 1.14.0-SNAPSHOT at 2024-06-30T13:00:04.112802098Z
FROM ubuntu:latest

LABEL "org.opencontainers.image.title"="jreleaser-slim"
LABEL "org.opencontainers.image.description"="Release projects quickly and easily with JReleaser"
LABEL "org.opencontainers.image.url"="https://jreleaser.org"
LABEL "org.opencontainers.image.licenses"="Apache-2.0"
LABEL "org.opencontainers.image.version"="1.13.1"
LABEL "org.opencontainers.image.revision"="5542956c0a386c559a22840e3d323d6b59ab9f65"

ARG DEBIAN_FRONTEND=noninteractive
ENV TZ=Europe/Zurich
RUN apt-get update && apt-get install -y unzip binutils fakeroot rpm

COPY assembly/* /

RUN unzip jreleaser-standalone-1.13.1-linux-x86_64.zip && \
    rm jreleaser-standalone-1.13.1-linux-x86_64.zip && \
    chmod +x jreleaser-standalone-1.13.1-linux-x86_64/bin/jreleaser && \
    chmod +x jreleaser-standalone-1.13.1-linux-x86_64/bin/java && \
    mv /jreleaser-entrypoint.sh /jreleaser-standalone-1.13.1-linux-x86_64/bin && \
    chmod +x /jreleaser-standalone-1.13.1-linux-x86_64/bin/jreleaser-entrypoint.sh && \
    mv /jreleaser-standalone-1.13.1-linux-x86_64 /jreleaser

ENV PATH="${PATH}:/jreleaser/bin"

VOLUME /workspace

ENTRYPOINT ["/jreleaser/bin/jreleaser-entrypoint.sh"]
CMD ["/jreleaser/bin/jreleaser"]
