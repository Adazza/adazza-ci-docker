FROM buildpack-deps:bionic

ENV CI True

ENV TZ=Etc/UTC
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone
RUN curl -sL https://deb.nodesource.com/setup_10.x | bash -
RUN wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add -
RUN sh -c 'echo "deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main" >> /etc/apt/sources.list.d/google.list'
RUN apt-get update
RUN apt-get install -y nodejs firefox google-chrome-stable google-chrome-unstable awscli
RUN npm i -g npm@'~6.5.0' yarn@'1.12.3' n@'2.1.12'

RUN n 10.15.0

RUN mkdir /project
ENTRYPOINT ["bash"]
WORKDIR /project
