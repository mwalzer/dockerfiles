FROM openms/library:v2.1.0

LABEL software="pyOpenMS"
LABEL software.version="v2.1.0"
LABEL website="https://www.OpenMS.de"
LABEL documentation="https://www.OpenMS.de/documentation/"
LABEL tags="proteomics, mass spectrometry"
LABEL license="https://raw.githubusercontent.com/OpenMS/OpenMS/develop/License.txt"
LABEL base.image="ubuntu:14.04"

ENV DEBIAN_FRONTEND noninteractive
USER root

WORKDIR /openms-build

RUN apt-get update -y 
RUN apt-get install -y python-pip python-dev python-numpy
RUN pip install nose
RUN pip install -U setuptools
RUN pip install Cython
RUN pip install 'autowrap==0.9.2'
RUN cmake -DCMAKE_PREFIX_PATH="/contrib-build/;/usr/;/usr/local" -DBOOST_USE_STATIC=OFF -DHAS_XSERVER=Off -DPYOPENMS=On ../OpenMS

# make OpenMS library
RUN make pyopenms

# install
WORKDIR /openms-build/pyOpenMS
RUN python setup.py install
WORKDIR /
ENV PATH="/openms-build/bin/:${PATH}"
ENV LD_LIBRARY_PATH="/OpenMS/lib/:${LD_LIBRARY_PATH}"
