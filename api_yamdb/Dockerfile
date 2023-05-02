FROM python:3.7

WORKDIR /app

COPY . /app

RUN python -m pip install --upgrade pip

RUN pip3 install -r requirements.txt --no-cache-dir

COPY ./ /app

LABEL author='Nastya' link_to_github='https://github.com/nastasiatr'

CMD ["gunicorn", "api_yamdb.wsgi:application", "--bind", "0:8000" ]