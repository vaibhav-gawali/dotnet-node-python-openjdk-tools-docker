# Optimized Dockerfile for containerized Development Environment

ARG UBUNTU_VERSION=25.10
FROM ubuntu:${UBUNTU_VERSION}

# Metadata labels for Docker Scout
LABEL maintainer="vaibhav@vaibhavgawali.net" \
      version="1.0.0" \
      description=".NET 10 MAUI Hybrid Android & Blazor Web with Node.js & Python." \
      vendor="Vaibhav M. Gawali" \
      org.opencontainers.image.source="https://github.com/vaibhav-gawali/dotnet-node-python-openjdk-tools-docker" \
      org.opencontainers.image.documentation="https://github.com/vaibhav-gawali/dotnet-node-python-openjdk-tools-docker/blob/main/README.md"

# Build arguments for version control
ARG DOTNET_VERSION=10.0
ARG NODE_VERSION=22
ARG PYTHON_VERSION=3.14
ARG JAVA_VERSION=21-jdk-headless

# Environment variables for build and runtime
ENV DEBIAN_FRONTEND=noninteractive \
    LANG=C.UTF-8 \
    LC_ALL=C.UTF-8 \
    DOTNET_ROOT=/usr/share/dotnet \
    PATH="/opt/venv/bin:/usr/share/dotnet:${PATH}" \
    DOTNET_SKIP_FIRST_TIME_EXPERIENCE=true \
    DOTNET_CLI_TELEMETRY_OPTOUT=true \
    PYTHONUNBUFFERED=1 \
    PYTHONDONTWRITEBYTECODE=1 \
    PIP_NO_CACHE_DIR=1 \
    PIP_DISABLE_PIP_VERSION_CHECK=1

# Install all system dependencies, runtimes, and SDKs in a single optimized layer
RUN apt-get update && \
    apt-get install -y --no-install-recommends \
        ca-certificates \
        curl \
        wget \
        git \
        gnupg \
        software-properties-common \
        apt-transport-https \
        openjdk-${JAVA_VERSION} \
        python${PYTHON_VERSION} \
        python3-pip \
        python${PYTHON_VERSION}-venv \
        python3-full \
        dotnet-sdk-${DOTNET_VERSION} \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

# Install Node.js and update npm in a single layer
RUN curl -fsSL https://deb.nodesource.com/setup_${NODE_VERSION}.x | bash - && \
    apt-get install -y --no-install-recommends nodejs && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* && \
    npm cache clean --force && \
    npm install -g npm@latest && \
    npm cache clean --force

# Create Python virtual environment and upgrade pip
RUN python3 -m venv /opt/venv && \
    /opt/venv/bin/pip install --no-cache-dir --upgrade \
        pip \
        setuptools \
        wheel && \
    rm -rf /root/.cache/pip /tmp/*

# Create non-root user and configure all permissions in one layer
RUN groupadd -g 1001 appuser && \
    useradd -r -u 1001 -g appuser appuser && \
    mkdir -p /home/appuser /workspace /home/appuser/.npm-global /home/appuser/.npm-cache && \
    chown -R appuser:appuser /home/appuser /workspace /opt/venv

# Switch to non-root user
USER appuser

# Configure npm for non-root user and update PATH
RUN npm config set prefix '/home/appuser/.npm-global' && \
    npm config set cache '/home/appuser/.npm-cache'

ENV PATH="/home/appuser/.npm-global/bin:${PATH}"

# Verify all installations (build-time check)
RUN dotnet --version && \
    git --version && \
    java -version && \
    node --version && \
    npm --version && \
    python3 --version && \
    pip --version

# Set working directory and volume
WORKDIR /workspace
VOLUME ["/workspace"]

# Default command
CMD ["/bin/bash"]
