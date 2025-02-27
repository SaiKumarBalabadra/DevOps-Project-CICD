FROM python:3.11-alpine AS builder
RUN apk add --no-cache gcc musl-dev python3-dev linux-headers
WORKDIR /app
COPY src/requirements.txt .
# First, explicitly remove any existing setuptools
RUN pip uninstall -y setuptools
# Then install the fixed version
RUN pip install --no-cache-dir setuptools==70.0.0
# Now install other dependencies
RUN pip install --no-cache-dir --upgrade pip
RUN pip install --no-cache-dir -r requirements.txt
# Final check to ensure correct version
RUN pip install --no-cache-dir --upgrade setuptools==70.0.0

FROM python:3.11-alpine
WORKDIR /app
COPY --from=builder /usr/local/lib/python3.11/site-packages /usr/local/lib/python3.11/site-packages
COPY --from=builder /usr/local/bin /usr/local/bin
COPY src/ /app
# Verify setuptools version in final image
RUN pip show setuptools | grep "Version"
CMD ["python", "run.py"]
