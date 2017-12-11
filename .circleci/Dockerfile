FROM ruby:2.3.3-slim

ENV PACKAGES build-essential libpq-dev netcat git python3 python-pip python-dev apt-utils wget
RUN apt-get update && apt-get install -qq -y $PACKAGES --fix-missing --no-install-recommends

# Configure/Install Postgres Repos/Deps
ENV PG_PACKAGES postgresql-9.6 postgresql-9.6-postgis-2.4
RUN echo deb http://apt.postgresql.org/pub/repos/apt jessie-pgdg main > /etc/apt/sources.list.d/jessie-pgdg.list && \
      wget --quiet -O - http://apt.postgresql.org/pub/repos/apt/ACCC4CF8.asc | apt-key add -
RUN apt-get update && apt-get -t jessie-pgdg install -qq -y $PG_PACKAGES --fix-missing --no-install-recommends

RUN gem install bundler

RUN pip install -U pip
RUN pip install poirot
