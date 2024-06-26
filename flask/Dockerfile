FROM python

COPY . /app
WORKDIR /app

RUN pip install flask

ENTRYPOINT ["flask", "run", "--host=0.0.0.0"]