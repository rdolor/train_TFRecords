FROM python:3.6-slim-stretch as pytrain-base
#ADD requirements.txt requirements.txt
RUN apt-get update -qq && \
    apt-get install -yqq --no-install-recommends vim &&  \
    apt-get install -yqq gcc && \
    apt-get install make &&\
    #pip install --no-cache-dir -r requirements.txt && \
    #Clean-up
    rm -rf /var/lib/apt/lists/* && \
    apt-get clean

RUN pip install --upgrade pip
RUN pip install pipenv
  
ADD Pipfile.lock . 
ADD Pipfile . 
RUN pipenv install --system --deploy --ignore-pipfile

ADD . .
#ADD crontab /etc/cron.d/cronlist
#RUN crontab /etc/cron.d/cronlist
CMD ["make", "activate_flask"]
