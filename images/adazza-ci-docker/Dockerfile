FROM buildpack-deps:bionic

ENV CI True

# Docker prereq
RUN apt-get update
RUN apt-get install -y apt-transport-https ca-certificates curl software-properties-common
RUN curl -fsSL https://download.docker.com/linux/ubuntu/gpg | apt-key add -
RUN add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"

# Node prereq
RUN curl -sL https://deb.nodesource.com/setup_10.x | bash -

# Install OS deps
RUN apt-get update
RUN apt-get install -y nodejs docker-ce
RUN npm i -g npm yarn

RUN mkdir /project
ENTRYPOINT ["bash"]
WORKDIR /project
