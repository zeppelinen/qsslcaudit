# 
# Docker environment for QSSLCAUDIT testing
# Uses standard OpenSSL libraries
#
# Prepare image: docker build -t centos-7 -f path/to/Dockerfile .
# Run instance:  docker run --name centos-7 --rm -it centos-7
#

FROM centos:7 as stage1
# prebuild stage
RUN yum -y update && \
yum -y install epel-release && \
yum -y install make cmake qt5-qtbase-devel gnutls-devel openssl openssl-libs openssl-devel gcc gcc-c++

# add files
ADD . /qsslcaudit
WORKDIR /qsslcaudit
# build stage
RUN tools/install.sh
# postbuild stage
RUN echo post build

FROM centos:7
WORKDIR /root/


CMD ["/bin/true"]  