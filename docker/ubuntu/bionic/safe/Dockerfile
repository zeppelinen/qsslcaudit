# 
# Docker environment for QSSLCAUDIT testing
# Uses standard OpenSSL libraries
#
# Prepare image: docker build -t ubuntu-bionic -f path/to/Dockerfile .
# Run instance:  docker run --name ubuntu-bionic --rm -it ubuntu-bionic
#

FROM ubuntu:bionic as stage1
# prebuild stage
RUN apt-get update && apt-get -y install make cmake qtbase5-dev g++ libgnutls28-dev libssl-dev
# add files
ADD . /qsslcaudit
WORKDIR /qsslcaudit
# build stage
RUN tools/install.sh
# postbuild stage
RUN echo post build

FROM ubuntu:bionic

WORKDIR /root/

COPY --from=stage1 /usr/local/bin/qsslcaudit /usr/local/bin/

CMD ["/bin/true"]  