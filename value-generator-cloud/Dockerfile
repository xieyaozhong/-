FROM python:3.12-slim

ENV PYTHONDONTWRITEBYTECODE=1 \
    PYTHONUNBUFFERED=1

WORKDIR /app

COPY source.part* /tmp/value-generator/
RUN cat /tmp/value-generator/source.part* | base64 -d > /tmp/value-generator.zip \
    && python -m zipfile -e /tmp/value-generator.zip /app \
    && pip install --no-cache-dir -r /app/requirements.txt \
    && mkdir -p /app/data \
    && rm -rf /tmp/value-generator /tmp/value-generator.zip

EXPOSE 8000

CMD ["sh", "-c", "uvicorn app.main:app --host 0.0.0.0 --port ${PORT:-8000} --proxy-headers --forwarded-allow-ips='*'"]
