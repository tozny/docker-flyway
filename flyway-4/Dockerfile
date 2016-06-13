# Dockerfile written by Eric Mann <eric@tozny.com>
#
# Work derived from ShouldBee
# Copyright (c) 2016 Tozny, LLC

FROM tozny/java:latest

ADD http://repo1.maven.org/maven2/org/flywaydb/flyway-commandline/4.0.2/flyway-commandline-4.0.2.zip /flyway.zip

RUN unzip /flyway.zip \
    && rm /flyway.zip \
    && mv /flyway-4.0.2 /flyway \
    && ln -s /flyway/flyway /usr/local/bin/flyway

# A simple testing
RUN flyway 2>&1 | grep "Flyway 4.0.2"

WORKDIR /flyway
ENTRYPOINT ["flyway"]
CMD ["--help"]