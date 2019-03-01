FROM buildpack-deps:bionic

# Docker prereq
ENV TZ=Etc/UTC
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone
RUN apt-get update
RUN apt-get install -y apt-transport-https ca-certificates curl software-properties-common
RUN apt-get install -y openjdk-8-jdk
RUN apt-get install -y python-pip
RUN pip install boto3 boto botocore awscli
RUN pip install dnspython

RUN mkdir -p /opt/adazza/bin/
RUN mkdir -p /opt/adazza/lib/
COPY files/start-adazza-service /opt/adazza/bin/start-adazza-service
RUN chmod +x /opt/adazza/bin/start-adazza-service

WORKDIR /opt/adazza/
