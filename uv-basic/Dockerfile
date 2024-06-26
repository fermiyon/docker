FROM python

COPY . /app
WORKDIR /app

# ref: https://stackoverflow.com/questions/48561981/activate-python-virtualenv-in-dockerfile
RUN python -m venv /opt/venv
# Enable venv
ENV PATH="/opt/venv/bin:$PATH"

RUN pip install uv
RUN uv pip install flask

ENTRYPOINT ["flask", "run", "--host=0.0.0.0"]