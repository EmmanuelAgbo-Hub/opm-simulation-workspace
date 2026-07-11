# Use a modern, stable Ubuntu base image
FROM mcr.microsoft.com/devcontainers/base:ubuntu-22.04

# Prevent interactive prompts during installation
ENV DEBIAN_FRONTEND=noninteractive

# Install essential build tools and software-properties-common
RUN apt-get update && apt-get install -y --no-install-recommends \
    build-essential \
    cmake \
    git \
    gnupg2 \
    software-properties-common \
    wget \
    pkg-config \
    && rm -rf /var/lib/apt/lists/*

# Add the official OPM PPA repository and install OPM dependencies
# This includes DUNE, MPI, and Zoltan libraries required by Flow/OPM Common
RUN add-apt-repository ppa:opm/ppa \
    && apt-get update \
    && apt-get install -y --no-install-recommends \
    libopm-common-dev \
    libopm-material-dev \
    libopm-simulators-dev \
    opm-simulators \
    python3-opm \
    && rm -rf /var/lib/apt/lists/*

# (Optional) If you plan to use Python tools like ResInsight or opm-utilities
RUN apt-get update && apt-get install -y --no-install-recommends \
    python3-pip \
    python3-numpy \
    python3-pandas \
    && rm -rf /var/lib/apt/lists/*
