FROM buildpack-deps:bionic

ENV CI True

# Docker prereq
ENV TZ=Etc/UTC
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone
RUN apt-get update
RUN apt-get install -y apt-transport-https ca-certificates curl software-properties-common awscli unzip
RUN apt-get install -y openjdk-8-jdk

RUN wget https://releases.hashicorp.com/packer/1.3.0/packer_1.3.0_linux_amd64.zip -O /tmp/packer.zip
RUN unzip /tmp/packer.zip -d /usr/local/bin/
RUN chmod '0755' /usr/local/bin/packer
RUN rm /tmp/packer.zip

RUN mkdir /project
ENTRYPOINT ["bash"]
WORKDIR /project
