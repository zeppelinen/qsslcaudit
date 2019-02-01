# 
# Docker environment for QSSLCAUDIT testing
# Uses standard OpenSSL libraries
#
# Prepare image: docker build -t kalilinux-latest -f path/to/Dockerfile .
# Run instance:  docker run --name kalilinux-latest --rm -it kalilinux-latest
#

FROM kalilinux/kali-linux-docker:latest as stage1
# prebuild stage
RUN apt-get update && apt-get -y install make cmake qt5-default g++ libgnutls28-dev libssl-dev
# add files
ADD . /qsslcaudit
WORKDIR /qsslcaudit
# build stage
RUN tools/install.sh
# postbuild stage
RUN echo post build

FROM kalilinux/kali-linux-docker:latest

WORKDIR /root/

COPY --from=stage1 /usr/local/bin/qsslcaudit /usr/local/bin/

CMD ["/bin/true"]  