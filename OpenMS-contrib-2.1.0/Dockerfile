#OpenMS contrib container image 
FROM ubuntu:16.04

LABEL software="OpenMS-contrib"
LABEL software.version="2.1.0"
LABEL website="https://www.OpenMS.de"
LABEL documentation="https://www.OpenMS.de/documentation/"
LABEL tags="Proteomics"

MAINTAINER Mathias Walzer <walzer@ebi.ac.uk>

ENV DEBIAN_FRONTEND noninteractive
USER root 
RUN apt-get update && apt-get install -y --no-install-recommends \
  git ca-certificates build-essential cmake autoconf patch libtool automake && \
  cd /opt/ && \
  git clone https://github.com/OpenMS/contrib.git openms-contrib-src && \
  cd openms-contrib-src && \
  git checkout tags/Release2.1.0 && \
  mkdir /opt/openms-contrib && cd /opt/openms-contrib/ && \
  cmake -DBUILD_TYPE=ALL ../openms-contrib-src -DNUMBER_OF_JOBS=2 && make && \
  rm -rf /opt/openms-contrib-src/ && rm -rf /opt/openms-contrib/src/ && \
  apt-get purge -y git build-essential cmake autoconf patch libtool automake && \
  apt-get autoremove -y && \
  rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* /var/lib/{cache,log}
WORKDIR /



