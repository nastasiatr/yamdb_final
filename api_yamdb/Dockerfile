FROM python:3.7-slim

WORKDIR /app

COPY api_yamdb/requirements.txt .

RUN python -m pip install --upgrade pip

RUN pip3 install -r /app/requirements.txt --no-cache-dir

COPY api_yamdb/ /app

LABEL author='Nastya' link_to_github='https://github.com/nastasiatr'

CMD ["gunicorn", "api_yamdb.wsgi:application", "--bind", "0:8000" ]