FROM ubuntu:16.04

RUN apt-get update && apt-get -y install \
    wget \
    git \
    build-essential \
    libtool \
    mercurial \
    mercurial-common \
    gettext \
    python \
    python-setuptools \ 
    python-pip \
    ca-certificates

RUN cp -rp /etc/ssl/certs /usr/ \
    && mkdir -p /usr/python13

RUN wget https://www.openssl.org/source/openssl-1.1.1-pre8.tar.gz && \
    tar xvzf openssl-1.1.1-pre8.tar.gz && \
    cd openssl-1.1.1-pre8 && ./Configure linux-x86_64 --prefix=/usr --openssldir=/usr && make && make install

RUN apt remove -y bzip2 && \
    wget http://bzip.org/1.0.6/bzip2-1.0.6.tar.gz && \
    tar xvzf bzip2-1.0.6.tar.gz && \
    cd bzip2-1.0.6 && \
    make -f Makefile-libbz2_so && \
    make install PREFIX="/usr"

RUN wget https://www.python.org/ftp/python/2.7.15/Python-2.7.15.tar.xz && \
    tar -xvJf Python-2.7.15.tar.xz && cd Python-2.7.15 && \
    ./configure --prefix=/usr/python13 CFLAGS="-I/usr" LDFLAGS="-L/usr" && \
    make && make install

RUN hg clone https://www.mercurial-scm.org/repo/hg-committed

