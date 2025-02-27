FROM python:3.11-alpine AS builder
RUN apk add --no-cache gcc musl-dev python3-dev linux-headers
WORKDIR /app
COPY src/requirements.txt .
RUN pip install --no-cache-dir --upgrade pip setuptools>=70.0.0
RUN pip install --no-cache-dir -r requirements.txt

FROM python:3.11-alpine
WORKDIR /app
COPY --from=builder /usr/local/lib/python3.11/site-packages /usr/local/lib/python3.11/site-packages
COPY --from=builder /usr/local/bin /usr/local/bin
COPY src/ /app
CMD ["python", "run.py"]
