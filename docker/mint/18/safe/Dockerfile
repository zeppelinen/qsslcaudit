# 
# Docker environment for QSSLCAUDIT testing
# Uses standard OpenSSL libraries
#
# Prepare image: docker build -t mint-18 -f path/to/Dockerfile .
# Run instance:  docker run --name mint-18 --rm -it mint-18
#

FROM vcatechnology/linux-mint:18 as stage1
# prebuild stage
RUN apt-get update && apt-get -y install make cmake qtbase5-dev g++ libgnutls-dev libssl-dev
# add files
ADD . /qsslcaudit
WORKDIR /qsslcaudit
# build stage
RUN tools/install.sh
# postbuild stage
RUN echo post build

FROM vcatechnology/linux-mint:18

WORKDIR /root/

COPY --from=stage1 /usr/local/bin/qsslcaudit /usr/local/bin/

CMD ["/bin/true"]  