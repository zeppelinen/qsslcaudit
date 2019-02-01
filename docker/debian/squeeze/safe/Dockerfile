# 
# Docker environment for QSSLCAUDIT testing
# Uses standard OpenSSL libraries
#
# Prepare image: docker build -t debian-squeeze -f path/to/Dockerfile .
# Run instance:  docker run --name debian-squeeze --rm -it debian-squeeze
#

FROM debian:squeeze
# prebuild stage
RUN apt-get update && apt-get -y install make cmake qt5-default g++ libgnutls28-dev libssl-dev
# add files
ADD . /qsslcaudit
WORKDIR /qsslcaudit
# build stage
RUN tools/install.sh
# postbuild stage
RUN echo post build
