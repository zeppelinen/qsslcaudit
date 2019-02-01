# 
# Docker environment for QSSLCAUDIT testing
# Uses standard OpenSSL libraries
#
# Prepare image: docker build -t ubuntu-xenial -f path/to/Dockerfile .
# Run instance:  docker run --name ubuntu-xenial --rm -it ubuntu-xenial
#

FROM ubuntu:xenial as stage1
# prebuild stage
RUN apt-get update && apt-get -y install make cmake qtbase5-dev g++ libgnutls-dev libssl-dev
# add files
ADD . /qsslcaudit
WORKDIR /qsslcaudit
# build stage
RUN tools/install.sh
# postbuild stage
RUN echo post build

FROM ubuntu:xenial
WORKDIR /root/


CMD ["/bin/true"]  