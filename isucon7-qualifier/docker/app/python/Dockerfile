FROM python:3.6.2

ARG GIT_URL=https://github.com/isucon/isucon7-qualify.git

RUN git clone $GIT_URL /home/isucon/isubata
WORKDIR /home/isucon/isubata/webapp/python
RUN pip install -r requirements.txt
RUN pip install newrelic
COPY newrelic.ini .
EXPOSE 5000
ENV NEW_RELIC_CONFIG_FILE=newrelic.ini
ENTRYPOINT ["newrelic-admin", "run-program", "gunicorn", "app:app", "-b", "0.0.0.0:5000"]
CMD ["--workers=4", "--threads=4"]
