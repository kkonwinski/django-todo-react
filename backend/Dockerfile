FROM python:3.9-alpine

ENV PYTHONUNBUFFERED 1
ENV PYTHONDONTWRITEBYTECODE 1

WORKDIR /app/backend

COPY requirements.txt /app/backend/

# Install required packages and remove unnecessary packages
RUN apk add --no-cache \
        postgresql-dev \
        libpq \
        gcc \
        python3-dev \
        musl-dev \
    && pip install --no-cache-dir --upgrade pip \
    && pip install --no-cache-dir -r requirements.txt \
    && apk del gcc python3-dev musl-dev


COPY . /app/backend/

CMD [ "python", "manage.py", "runserver", "0.0.0.0:8000" ]
