FROM python:3.8.5-slim

RUN apt-get -y update --fix-missing && apt-get -y upgrade

# Dependancies
RUN apt-get install -y \
    make \
    gcc \
    clang \
    valgrind \
    git \
    build-essential \
    software-properties-common \
    wget \
    curl

RUN curl -sSL https://raw.githubusercontent.com/python-poetry/poetry/master/get-poetry.py | python
ENV PATH="/root/.poetry/bin:$PATH"

RUN mkdir /app
COPY . /app
WORKDIR /app

# Defaults
WORKDIR /app/
RUN python -m pip install --upgrade pip
RUN poetry install -v

CMD ["poetry", "run", "./hello/main"]
