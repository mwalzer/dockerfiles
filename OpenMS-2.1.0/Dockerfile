#OpenMS 2.1.0 container basing upon OpenMS-contrib image
FROM openms-contrib-2.1.0  

LABEL software="OpenMS"
LABEL software.version="2.1.0"
LABEL website="https://www.OpenMS.de"
LABEL documentation="https://www.OpenMS.de/documentation/"
LABEL tags="Proteomics"

MAINTAINER Mathias Walzer <walzer@ebi.ac.uk>

ENV DEBIAN_FRONTEND noninteractive
USER root 
RUN apt-get update && apt-get install -y --no-install-recommends \
  git ca-certificates build-essential cmake autoconf patch libtool automake \
  libqt4-dev libqtwebkit-dev libqt4-opengl-dev libgomp1 && \
  cd /opt/ && \
  git clone https://github.com/OpenMS/OpenMS.git openms-src && \
  cd /opt/openms-src/ && \
  git checkout tags/Release2.1.0 && cd /opt/ && mkdir openms-build && \
  cd /opt/openms-build/ && \
  cmake -DCMAKE_PREFIX_PATH="/opt/openms-contrib/;/usr/;/usr/local" \
  -DCMAKE_INSTALL_PREFIX="/usr" \
  -DBOOST_USE_STATIC=ON \
  -DHAS_XSERVER=Off ../openms-src && make -j2 && make install && \
  rm -rf /opt/openms* && \
  apt-get purge -y git build-essential cmake autoconf patch libtool automake && \
  apt-get autoremove -y && \
  rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* /var/lib/{cache,log}
ENV PATH /usr/bin/:$PATH
ENV LD_LIBRARY_PATH /usr/lib:$LD_LIBRARY_PATH
WORKDIR /



