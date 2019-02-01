# 
# Docker environment for QSSLCAUDIT testing
# Uses standard OpenSSL libraries
#
# Prepare image: docker build -t fedora-28 -f path/to/Dockerfile .
# Run instance:  docker run --name fedora-28 --rm -it fedora-28
#

FROM fedora:28 as stage1
# prebuild stage
RUN dnf -y update && \
dnf -y install make cmake qt5-qtbase-devel gnutls-devel openssl openssl-libs openssl-devel gcc gcc-c++

# add files
ADD . /qsslcaudit
WORKDIR /qsslcaudit
# build stage
RUN tools/install.sh
# postbuild stage
RUN echo post build

FROM fedora:28
WORKDIR /root/


CMD ["/bin/true"]  