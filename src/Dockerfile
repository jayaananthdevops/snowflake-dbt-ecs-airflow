# Copyright Amazon.com, Inc. or its affiliates. All Rights Reserved.
# SPDX-License-Identifier: MIT-0

FROM python:3.8-slim-buster

ADD dbt-project /dbt-project

# Update and install system packages
RUN apt-get update -y && \
  apt-get install --no-install-recommends -y -q \
  git libpq-dev python-dev && \
  apt-get clean && \
  rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

# Install DBT
RUN pip install -U pip
RUN pip install dbt-core
RUN pip install dbt-snowflake

RUN mkdir -p /root/.dbt
COPY /dbt-project/profiles.yml /root/.dbt/profiles.yml
WORKDIR /dbt-project
#CMD ["/bin/bash"]
#ENTRYPOINT ["dbt","run"]

