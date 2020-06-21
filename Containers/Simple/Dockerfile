FROM ubuntu:18.04
MAINTAINER Joshua Haywworth <jhayworth@btisinc.com>

# Setup app user
ENV HOME /home/simple-user
RUN groupadd -g 11000 simple
RUN useradd -c "simple application user" -d $HOME -u 11000 -g 11000 -m simple-user
