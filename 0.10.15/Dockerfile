FROM ubuntu:latest AS stress-ng
ENV RELEASE_VERSION=0.10.15
ENV SHELL=/bin/bash


RUN apt-get -y update \
    && apt-get install -y apt-utils \ 
    && apt-get install -y libaio-dev \
     libapparmor-dev \
     libattr1-dev \
     libbsd-dev \
     libcap-dev \
     libgcrypt11-dev \
     libipsec-mb-dev \
     libjudy-dev \
     libkeyutils-dev \
     libsctp-dev \
     zlib1g-dev \
     bash g++ make wget lzma xz-utils \
    && cd /tmp && wget https://kernel.ubuntu.com/~cking/tarballs/stress-ng/stress-ng-${RELEASE_VERSION}.tar.xz \
    && tar xJvf stress-ng-${RELEASE_VERSION}.tar.xz && cd /tmp/stress-ng-${RELEASE_VERSION} \
    && make && make install 


FROM ubuntu:latest
RUN apt-get -y update \
    && apt-get install -y apt-utils \
    && apt-get install -y libaio-dev \
     libapparmor-dev \
     libattr1-dev \
     libbsd-dev \
     libcap-dev \
     libgcrypt11-dev \
     libipsec-mb-dev \
     libjudy-dev \
     libkeyutils-dev \
     libsctp-dev \
     zlib1g-dev
COPY --from=stress-ng /usr/share/man/man1/stress-ng.1.gz /usr/share/man/man1/stress-ng.1.gz
COPY --from=stress-ng /usr/share/bash-completion/completions/stress-ng /usr/share/bash-completion/completions/stress-ng
COPY --from=stress-ng /usr/bin/stress-ng /usr/bin/stress-ng
CMD ["/usr/local/bin/stress-ng"]
