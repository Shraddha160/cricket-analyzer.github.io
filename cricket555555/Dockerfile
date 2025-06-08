# Install system dependencies first
RUN apt-get update && apt-get install -y \
    python3-dev \
    python3-distutils \
    && rm -rf /var/lib/apt/lists/*

# Then create venv and install requirements
RUN --mount=type=cache,id=s/5e320008-89d7-4ab6-a9ac-d5e7ed64514c-/root/cache/pip,target=/root/.cache/pip \
    python -m venv --copies /opt/venv && \
    . /opt/venv/bin/activate && \
    pip install --upgrade pip && \
    pip install -r requirements.txt
