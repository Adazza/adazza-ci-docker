FROM buildpack-deps:bionic

ENV CI True

# Docker prereq
ENV TZ=Etc/UTC
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone
RUN apt-get update
RUN apt-get install -y apt-transport-https ca-certificates curl software-properties-common awscli
RUN apt-get install -y openjdk-8-jdk
RUN apt-get install -y unzip

RUN wget --quiet https://releases.hashicorp.com/packer/1.3.2/packer_1.3.2_linux_amd64.zip -O /tmp/packer.zip
RUN unzip /tmp/packer.zip -d /usr/local/bin/
RUN chmod '0755' /usr/local/bin/packer
RUN rm /tmp/packer.zip
RUN apt-get install -y python-pip
RUN pip install ansible==2.6.3
RUN pip install boto3 boto botocore
RUN pip install dnspython

RUN mkdir /project
ENTRYPOINT ["bash"]
WORKDIR /project
