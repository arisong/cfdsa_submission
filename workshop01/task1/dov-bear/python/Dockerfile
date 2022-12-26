FROM python:3.9.16

ARG APP_DIR=/app

RUN mkdir $APP_DIR

WORKDIR $APP_DIR

ADD main.py .
ADD requirements.txt .
ADD run.sh .
ADD utils.py .
ADD public public
ADD templates templates

RUN pip install -r requirements.txt

ENV PORT=3000 INSTANCE_NAME="dov-bear"

EXPOSE $PORT

HEALTHCHECK --interval=30s --timeout=30s --start-period=5s --retries=3 CMD curl http://localhost:${PORT}/healthz || exit 1

ENTRYPOINT ["python", "/app/main.py"]
