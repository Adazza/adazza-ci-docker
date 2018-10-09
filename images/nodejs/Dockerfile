FROM buildpack-deps:bionic

ENV CI True

ENV TZ=Etc/UTC
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone
RUN curl -sL https://deb.nodesource.com/setup_10.x | bash -
RUN apt-get update
RUN apt-get install -y nodejs awscli
RUN npm i -g npm@'~6.4.1' yarn@'~1.10.1' n

RUN n 10.11.0

RUN mkdir /project
ENTRYPOINT ["bash"]
WORKDIR /project
