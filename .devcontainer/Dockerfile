FROM odoo:19

USER root

# Install additional dependencies if needed
RUN apt-get update && apt-get install -y \
    build-essential \
    python3-dev \
    iputils-ping \
    git \
    wget \
    curl

# Clean up
RUN apt-get clean && rm -rf /var/lib/apt/lists/*
