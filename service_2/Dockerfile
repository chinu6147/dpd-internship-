FROM python:3.11-slim

WORKDIR /app

COPY pyproject.toml ./
COPY app.py ./

RUN pip install --no-cache-dir flask>=3.1.1

EXPOSE 8002
CMD ["python", "app.py"]