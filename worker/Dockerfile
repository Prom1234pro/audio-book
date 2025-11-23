FROM python:3.11-slim

WORKDIR /app

# Install system libs (ffmpeg required for audio)
RUN apt-get update && apt-get install -y ffmpeg build-essential && \
    rm -rf /var/lib/apt/lists/*

# Copy project
COPY . .

# Install dependencies
RUN pip install --upgrade pip && pip install -r requirements.txt

ENV PYTHONUNBUFFERED=1

CMD ["celery", "-A", "tasks", "worker", "--loglevel=INFO"]
