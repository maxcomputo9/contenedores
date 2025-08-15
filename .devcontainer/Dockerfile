# Use the specified base image
ARG VARIANT=20-bullseye
FROM mcr.microsoft.com/vscode/devcontainers/javascript-node:0-${VARIANT}

# Avoid prompts from apt
ENV DEBIAN_FRONTEND=noninteractive

# Update package list and install system dependencies
RUN apt-get update && \
    apt-get install -y --no-install-recommends \
        unzip \
        wget \
        curl && \
    apt-get clean -y && \
    rm -rf /var/lib/apt/lists/*

# Install PM2 globally
RUN npm install -g pm2

# Install common Node.js tools
RUN npm install -g nodemon yarn

# Set the environment variable back to default
ENV DEBIAN_FRONTEND=

# Create docker group (will be used by Docker-in-Docker feature)
RUN sudo groupadd -f docker
