FROM buildpack-deps:bionic

ENV CI True

# Docker prereq
ENV TZ=Etc/UTC
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone
RUN apt-get update
RUN apt-get install -y apt-transport-https ca-certificates curl software-properties-common awscli
RUN curl -fsSL https://download.docker.com/linux/ubuntu/gpg | apt-key add -
RUN add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"

# Node prereq
RUN curl -sL https://deb.nodesource.com/setup_10.x | bash -

# Install OS deps
RUN apt-get update
RUN apt-get install -y nodejs docker-ce awscli

# Versioned deps
RUN npm i -g npm@'~6.9.0' yarn@'1.13.0' n@'2.1.12'
RUN n 10.15.3

RUN mkdir /project
ENTRYPOINT ["bash"]
WORKDIR /project
