FROM python:3.7

WORKDIR /app

COPY requirements.txt /.

RUN python -m pip install --upgrade pip

RUN pip install -r /app/requirements.txt

COPY /api_yamdb/ .

LABEL author='Nastya' link_to_github='https://github.com/nastasiatr'

CMD ["gunicorn", "api_yamdb.wsgi:application", "--bind", "0:8000" ]