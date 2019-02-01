# 
# Docker environment for QSSLCAUDIT testing
# Uses standard OpenSSL libraries
#
# Prepare image: docker build -t debian-wheezy -f path/to/Dockerfile .
# Run instance:  docker run --name debian-wheezy --rm -it debian-wheezy
#

FROM debian:wheezy as stage1
# prebuild stage
RUN echo 'deb http://http.debian.net/debian wheezy-backports main' > /etc/apt/sources.list.d/wheezy-backports.list
RUN apt-get update && apt-get -y install make cmake qt5-default g++ libgnutls-dev libssl-dev
# add files
ADD . /qsslcaudit
WORKDIR /qsslcaudit
# build stage
RUN tools/install.sh
# postbuild stage
RUN echo post build

FROM debian:wheezy

WORKDIR /root/

COPY --from=stage1 /usr/local/bin/qsslcaudit /usr/local/bin/

CMD ["/bin/true"]  