FROM ubuntu:20.04

ARG DEBIAN_FRONTEND=noninteractive

RUN apt-get update \
  && apt-get -y upgrade \
  && apt-get install -y --no-install-recommends \
    build-essential \
    cmake \
    gdal-bin \
    libboost-dev \
    libboost-serialization-dev \
    libbz2-dev \
    libexpat1-dev \
    libgdal-dev \
    libssl-dev \
    python-dev \
    swig \
    wget \
  && rm -rf /var/lib/apt/lists/*

WORKDIR /build-phase
COPY . ./
RUN mkdir -p build \
  && cd build \
  && cmake .. \
  && make -j4 \
  && make install
RUN rm -r /build-phase

RUN useradd --create-home appuser
WORKDIR /home/appuser
USER appuser
