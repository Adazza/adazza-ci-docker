FROM buildpack-deps:bionic

ENV CI True

ENV TZ=Etc/UTC
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone
RUN curl -sL https://deb.nodesource.com/setup_10.x | bash -
RUN apt-get update
RUN apt-get install -y nodejs awscli
RUN npm i -g npm@'~6.8.0' yarn@'1.13.0' n@'2.1.12' renovate@'14.37.0'

RUN n 10.15.3

RUN mkdir /project
ENTRYPOINT ["bash"]
WORKDIR /project
