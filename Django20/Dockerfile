FROM python:3.10

ENV PYTHONUNBUFFERED=1

WORKDIR /app

RUN apt-get update && apt-get install
RUN  python -m pip install --upgrade pip
RUN pip install --upgrade pip "poetry==1.4.2"
RUN poetry config virtualenvs.create false --local


COPY pyproject.toml poetry.lock ./
RUN poetry install


COPY mysite .

CMD ["gunicorn", "mysite.wsgi:application", "--bind", "0.0.0.0:8000"]

