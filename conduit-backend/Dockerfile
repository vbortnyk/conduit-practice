FROM python:3.6-slim

WORKDIR /app

COPY requirements.txt .
RUN pip install -r requirements.txt

COPY . .

RUN useradd -m -r appuser && chown -R appuser:appuser /app

RUN mkdir -p /app/staticfiles \
    && chown -R appuser:appuser /app/staticfiles \
    && chmod -R 755 /app/staticfiles

COPY entrypoint.sh /entrypoint.sh
RUN chmod +x /entrypoint.sh && chown appuser:appuser /entrypoint.sh

USER appuser

EXPOSE 8000

ENTRYPOINT ["/entrypoint.sh"]

