# Generated with JReleaser 1.3.0-SNAPSHOT at 2022-10-30T12:12:20.961917986Z
FROM ubuntu:latest

LABEL "org.opencontainers.image.title"="jreleaser-slim"
LABEL "org.opencontainers.image.description"="Release projects quickly and easily with JReleaser"
LABEL "org.opencontainers.image.url"="https://jreleaser.org"
LABEL "org.opencontainers.image.licenses"="Apache-2.0"
LABEL "org.opencontainers.image.version"="1.3.0"
LABEL "org.opencontainers.image.revision"="6aa3ca4afff2a4ee2eab8efbe0bfac7feed85fe2"

ARG DEBIAN_FRONTEND=noninteractive
ENV TZ=Europe/Zurich
RUN apt-get update && apt-get install -y unzip binutils fakeroot rpm

COPY assembly/* /

RUN unzip jreleaser-standalone-1.3.0-linux-x86_64.zip && \
    rm jreleaser-standalone-1.3.0-linux-x86_64.zip && \
    chmod +x jreleaser-standalone-1.3.0-linux-x86_64/bin/jreleaser && \
    chmod +x jreleaser-standalone-1.3.0-linux-x86_64/bin/java && \
    mv /jreleaser-entrypoint.sh /jreleaser-standalone-1.3.0-linux-x86_64/bin && \
    chmod +x /jreleaser-standalone-1.3.0-linux-x86_64/bin/jreleaser-entrypoint.sh && \
    mv /jreleaser-standalone-1.3.0-linux-x86_64 /jreleaser

ENV PATH="${PATH}:/jreleaser/bin"

VOLUME /workspace

ENTRYPOINT ["/jreleaser/bin/jreleaser-entrypoint.sh"]
CMD ["/jreleaser/bin/jreleaser"]
