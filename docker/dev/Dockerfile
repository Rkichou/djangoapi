FROM python:3.11-slim

WORKDIR /code

# Installer les dépendances système
RUN apt-get update && apt-get install -y \
    netcat-openbsd \
    && rm -rf /var/lib/apt/lists/*


# Installer les dépendances Python
COPY requirements/dev.txt .
RUN pip install --upgrade pip && pip install -r dev.txt

COPY . .

# Script d'entrée
ENTRYPOINT ["/code/docker/entrypoint.sh"]
