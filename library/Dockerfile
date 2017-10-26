FROM openms/contrib:v2.0.1

LABEL software="OpenMS lib"
LABEL software.version="v2.0.1"
LABEL website="https://www.OpenMS.de"
LABEL documentation="https://www.OpenMS.de/documentation/"
LABEL tags="proteomics, mass spectrometry"
LABEL license="https://raw.githubusercontent.com/OpenMS/OpenMS/develop/License.txt"
LABEL base.image="ubuntu:14.04"

ENV DEBIAN_FRONTEND noninteractive

WORKDIR /
RUN git clone  --branch 'Release2.0.1' --single-branch --depth 1 https://github.com/OpenMS/OpenMS.git
#RUN mkdir OpenMS
RUN mkdir openms-build

WORKDIR /openms-build

#RUN cmake -DOPENMS_CONTRIB_LIBS="/contrib-build/lib/" -DCMAKE_PREFIX_PATH="/usr;/usr/local" -DBOOST_USE_STATIC=OFF -DWITH_GUI=OFF -DSEQAN_INCLUDE_DIR="/contrib-build/include/" -DEIGEN3_INCLUDE_DIR="/contrib-build/include/eigen3" -DWM5_INCLUDE_DIR="/contrib-build/include/" -DWM5_Wm5Core_LIBRARY="/contrib-build/include/" -DWM5_Wm5Mathematics_LIBRARY="/contrib-build/lib" -DWM5_Wm5Core_LIBRARY="/contrib-build/lib" /OpenMS
RUN cmake -DCMAKE_PREFIX_PATH="/contrib-build;/usr;/usr/local" -DBOOST_USE_STATIC=OFF /OpenMS

RUN make OpenMS
