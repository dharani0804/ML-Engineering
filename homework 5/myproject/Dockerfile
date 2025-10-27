
FROM agrigorev/zoomcamp-model:2025

WORKDIR /app

# Install system dependencies for building Python packages
RUN apt-get update && \
    apt-get install -y build-essential libffi-dev libssl-dev python3-dev curl && \
    rm -rf /var/lib/apt/lists/*

# Copy requirements and install
COPY requirements.txt /app/
RUN pip install --upgrade pip && pip install -r requirements.txt

# Copy FastAPI script and pipeline
COPY main.py /app/
COPY pipeline_v1.bin /app/

EXPOSE 8000

CMD ["uvicorn", "main:app", "--host", "0.0.0.0", "--port", "8000"]