FROM ubuntu:16.04

LABEL software="OpenMS contrib packages"
LABEL software.version="2.4.0"
#LABEL software.version="LFQtool2.4.0"
LABEL website="https://www.OpenMS.de"
LABEL documentation="https://www.OpenMS.de/documentation/"
LABEL tags="proteomics, mass spectrometry"
LABEL license="https://raw.githubusercontent.com/OpenMS/contrib/master/License.txt"
LABEL base.image="ubuntu:16.04"

ENV DEBIAN_FRONTEND noninteractive

USER root

RUN apt-get -y update

RUN apt-get install -y --no-install-recommends --no-install-suggests ca-certificates \
													git \
													build-essential \
													#cmake \
													wget \
													autoconf \
													patch \
													libtool \
													automake \
													libgomp1 \
													python-software-properties \
													qtbase5-dev \
													libqt5svg5-dev \
													libsvm-dev\
													libglpk-dev \
													zlib1g-dev \
													libxerces-c-dev \
													seqan-dev \
													libbz2-dev \
													coinor-libcoinmp-dev

RUN apt remove --purge --auto-remove cmake
RUN wget https://cmake.org/files/v3.14/cmake-3.14.5-Linux-x86_64.sh
RUN mkdir /opt/cmake && bash cmake-3.14.5-Linux-x86_64.sh --prefix=/opt/cmake --skip-license && ln -s /opt/cmake/bin/cmake /usr/local/bin/cmake

RUN git clone --depth 1 --branch 'master'  --single-branch https://github.com/OpenMS/contrib.git
#RUN git clone --branch 'master'  --single-branch https://github.com/OpenMS/contrib.git
#WORKDIR /contrib
#RUN git reset --hard 06e887232ed87631585027e1991ebaef098f7b06

RUN mkdir contrib-build

WORKDIR /contrib-build

RUN cmake -DBUILD_TYPE=ALL ../contrib && rm -rf archives src

WORKDIR /

