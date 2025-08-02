# Use the specified base image
ARG VARIANT=20-bullseye
FROM mcr.microsoft.com/vscode/devcontainers/javascript-node:0-${VARIANT}

# Avoid prompts from apt
ENV DEBIAN_FRONTEND=noninteractive

# Update package list, install system dependencies, and clean up
# Added: unzip, wget, curl (useful for scripts), and ensured docker.io is installed
RUN apt-get update && \
    apt-get install -y --no-install-recommends \
        docker.io \
        unzip \
        wget \
        curl && \
    apt-get clean -y && \
    rm -rf /var/lib/apt/lists/*

# Install PM2 globally
# This ensures 'pm2' command is available for your npm scripts
RUN npm install -g pm2

# (Optional) Pre-install common Node.js tools you might use
RUN npm install -g nodemon yarn

# Set the environment variable back to default (good practice)
ENV DEBIAN_FRONTEND=
