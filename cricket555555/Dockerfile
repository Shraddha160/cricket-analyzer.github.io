# Install system dependencies and ensure Python build tools are available
RUN apt-get update && \
    apt-get install -y --no-install-recommends \
    python3-dev \
    python3-distutils \
    python3-venv \
    build-essential \
    && rm -rf /var/lib/apt/lists/*

# Create virtual environment with system site packages temporarily
RUN python3 -m venv --system-site-packages /opt/venv && \
    . /opt/venv/bin/activate && \
    python3 -m pip install --upgrade pip setuptools wheel

# Now install your requirements with the cache mount
RUN --mount=type=cache,id=pip-cache,target=/root/.cache/pip \
    . /opt/venv/bin/activate && \
    pip install -r requirements.txt
