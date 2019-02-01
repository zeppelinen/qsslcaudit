# 
# Docker environment for QSSLCAUDIT testing
# Uses standard OpenSSL libraries
#
# Prepare image: docker build -t debian-stretch -f path/to/Dockerfile .
# Run instance:  docker run --name debian-stretch --rm -it debian-stretch
#

FROM debian:stretch as stage1
# prebuild stage
RUN apt-get update && apt-get -y install make cmake qt5-default g++ libgnutls28-dev libssl-dev
# add files
ADD . /qsslcaudit
WORKDIR /qsslcaudit
# build stage
RUN tools/install.sh
# postbuild stage
RUN echo post build

FROM debian:stretch

WORKDIR /root/

COPY --from=stage1 /usr/local/bin/qsslcaudit /usr/local/bin/

CMD ["/bin/true"]  