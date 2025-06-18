FROM python:3.11-slim

ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1

WORKDIR /code

RUN apt-get update && apt-get install -y \
    libpq-dev gcc \
    && rm -rf /var/lib/apt/lists/*

COPY requirements/prod.txt .
RUN pip install --upgrade pip && pip install -r prod.txt

COPY . .

RUN python manage.py collectstatic --noinput

CMD ["gunicorn", "myproject.wsgi:application", "--bind", "0.0.0.0:8000"]
