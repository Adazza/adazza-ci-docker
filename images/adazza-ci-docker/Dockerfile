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
RUN apt-get install -y nodejs docker-ce
RUN npm i -g npm yarn

RUN mkdir /project
ENTRYPOINT ["bash"]
WORKDIR /project
