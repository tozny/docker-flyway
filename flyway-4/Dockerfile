# Dockerfile written by Eric Mann <eric@tozny.com>
#
# Copyright (c) 2016 Tozny, LLC

FROM tozny/java:latest

ENV FLYWAY_VERSION 4.0.2
ENV FLYWAY_SQL_DIR /sql

RUN apk update && apk add --update wget ca-certificates && update-ca-certificates

RUN mkdir /opt \
    && wget https://repo1.maven.org/maven2/org/flywaydb/flyway-commandline/${FLYWAY_VERSION}/flyway-commandline-${FLYWAY_VERSION}.zip \
    && unzip flyway-commandline-${FLYWAY_VERSION}.zip -d /opt \
    && mv /opt/flyway-${FLYWAY_VERSION} /opt/flyway \
    && sed -i 's/bash/sh/' /opt/flyway/flyway \
    && echo "flyway.locations=filesystem:${FLYWAY_SQL_DIR}" > /opt/flyway/conf/flyway.conf \
    && echo "flyway.encoding=UTF-8" >> /opt/flyway/conf/flyway.conf

COPY flyway.sh /opt/flyway/flyway

# Default location for sql migrations
VOLUME /sql

MAINTAINER Eric Mann

ENTRYPOINT ["/opt/flyway/flyway"]

CMD ["info"]