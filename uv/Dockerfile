# Base image
FROM python:3.12 as build
# ref: https://dev.to/kummerer94/multi-stage-docker-builds-for-pyton-projects-using-uv-223g
ENV VIRTUAL_ENV=/opt/venv \
    PATH="/opt/venv/bin:$PATH"

ADD https://astral.sh/uv/install.sh /install.sh
RUN chmod -R 655 /install.sh && /install.sh && rm /install.sh
COPY ./requirements.txt .
RUN /root/.cargo/bin/uv venv /opt/venv && \
    /root/.cargo/bin/uv pip install --no-cache -r requirements.txt

# App image
FROM python:3.12-slim-bookworm
COPY --from=build /opt/venv /opt/venv

# Activate the virtualenv in the container
# See here for more information:
# https://pythonspeed.com/articles/multi-stage-docker-python/
ENV PATH="/opt/venv/bin:$PATH"

COPY . /app
WORKDIR /app

ENTRYPOINT ["flask", "run", "--host=0.0.0.0"]