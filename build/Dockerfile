FROM python:3.11-alpine AS builder
RUN apk add --no-cache gcc musl-dev python3-dev linux-headers
WORKDIR /app
COPY src/requirements.txt .
# Create a virtual environment to isolate dependencies
RUN python -m venv /venv
# Install into the virtual environment
RUN /venv/bin/pip install --no-cache-dir --upgrade pip
RUN /venv/bin/pip install --no-cache-dir setuptools==70.0.0
RUN /venv/bin/pip install --no-cache-dir -r requirements.txt

FROM python:3.11-alpine
WORKDIR /app
# Copy the virtual environment
COPY --from=builder /venv /venv
COPY src/ /app
# Use the virtual environment's Python
CMD ["/venv/bin/python", "run.py"]
