FROM odoo:18

USER root

# Install additional dependencies if needed
RUN apt-get update && apt-get install -y \
    build-essential \
    python3-dev \
    iputils-ping \
    git

# Clean up
RUN apt-get clean && rm -rf /var/lib/apt/lists/*
