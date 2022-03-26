# Generated with JReleaser 1.0.0-SNAPSHOT at 2022-03-26T09:55:36.29189Z
FROM ubuntu:latest

LABEL "org.opencontainers.image.title"="jreleaser-slim"
LABEL "org.opencontainers.image.description"="Release projects quickly and easily with JReleaser"
LABEL "org.opencontainers.image.url"="https://jreleaser.org"
LABEL "org.opencontainers.image.licenses"="Apache-2.0"
LABEL "org.opencontainers.image.version"="1.0.0-RC1"
LABEL "org.opencontainers.image.revision"="085a05ba8a66370d4c6c139dafad078d64a2dd8f"

ARG DEBIAN_FRONTEND=noninteractive
ENV TZ=Europe/Zurich
RUN apt-get update && apt-get install -y unzip binutils fakeroot rpm

COPY assembly/* /

RUN unzip jreleaser-standalone-1.0.0-RC1-linux-x86_64.zip && \
    rm jreleaser-standalone-1.0.0-RC1-linux-x86_64.zip && \
    chmod +x jreleaser-standalone-1.0.0-RC1-linux-x86_64/bin/jreleaser && \
    chmod +x jreleaser-standalone-1.0.0-RC1-linux-x86_64/bin/java && \
    mv /jreleaser-entrypoint.sh /jreleaser-standalone-1.0.0-RC1-linux-x86_64/bin && \
    chmod +x /jreleaser-standalone-1.0.0-RC1-linux-x86_64/bin/jreleaser-entrypoint.sh

ENV PATH="${PATH}:/jreleaser-standalone-1.0.0-RC1-linux-x86_64/bin"

VOLUME /workspace

ENTRYPOINT ["/jreleaser-standalone-1.0.0-RC1-linux-x86_64/bin/jreleaser-entrypoint.sh"]
CMD ["/jreleaser-standalone-1.0.0-RC1-linux-x86_64/bin/jreleaser"]
