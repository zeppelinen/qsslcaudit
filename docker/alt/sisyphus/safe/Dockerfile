# 
# Docker environment for QSSLCAUDIT testing
# Uses standard OpenSSL libraries
#
# Prepare image: docker build -t alt-sisyphus -f path/to/Dockerfile .
# Run instance:  docker run --name alt-sisyphus --rm -it alt-sisyphus
#

FROM alt:sisyphus as stage1
# prebuild stage
RUN apt-get update && apt-get -y install make cmake qt5-base-devel gcc-c++ libgnutls-devel libssl-devel
# add files
ADD . /qsslcaudit
WORKDIR /qsslcaudit
# build stage
RUN tools/install.sh
# postbuild stage
RUN echo post build

FROM alt:sisyphus

WORKDIR /root/

COPY --from=stage1 /usr/local/bin/qsslcaudit /usr/local/bin/

CMD ["/bin/true"]  