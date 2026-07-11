# Use the clean, official Ubuntu image to completely bypass systemd/resolvconf conflicts
FROM ubuntu:22.04

# Prevent interactive prompts during installation
ENV DEBIAN_FRONTEND=noninteractive

# Install core development tools and repository management utilities
RUN apt-get update && apt-get install -y --no-install-recommends \
    build-essential \
    cmake \
    git \
    gnupg2 \
    software-properties-common \
    wget \
    pkg-config \
    ca-certificates \
    && rm -rf /var/lib/apt/lists/*

# Add the official OPM PPA repository and install the simulation engine stack
RUN add-apt-repository ppa:opm/ppa \
    && apt-get update \
    && apt-get install -y --no-install-recommends \
    libopm-common-dev \
    libopm-material-dev \
    libopm-simulators-dev \
    opm-simulators \
    python3-opm \
    && rm -rf /var/lib/apt/lists/*
