FROM ubuntu:18.04
MAINTAINER Joshua Haywworth <jhayworth@btisinc.com>

# Adding Label to Filter Container Types
LABEL ContainerType=Service

# Versions
ENV CONSUL_VERSION 1.6.3

# Turn off .NET Core telemetry collection
ENV DOTNET_CLI_TELEMETRY_OPTOUT 1
ENV ASPNETCORE_URLS "http://*:3000"

# update and install misc linux packages not included in base image
ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update \
    && apt-get install -y --no-install-recommends apt-transport-https ca-certificates unzip bzip2 libuv1 libuv1-dev wget curl nano \
    && rm -rf /var/lib/apt/lists/*

# Application directory
RUN mkdir /app
WORKDIR /app

# Setup app user
ENV HOME /home/simple-user
RUN groupadd -g 11000 simple
RUN useradd -c "simple application user" -d $HOME -u 11000 -g 11000 -m simple-user

# Consul installation
RUN wget https://releases.hashicorp.com/consul/${CONSUL_VERSION}/consul_${CONSUL_VERSION}_linux_amd64.zip
RUN unzip consul_${CONSUL_VERSION}_linux_amd64.zip
RUN mv consul /bin/

# Package Cleanup
RUN rm consul_${CONSUL_VERSION}_linux_amd64.zip
