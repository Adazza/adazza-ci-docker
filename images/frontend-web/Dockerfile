FROM buildpack-deps:bionic

ENV CI True

RUN curl -sL https://deb.nodesource.com/setup_10.x | bash -
RUN wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add -
RUN sh -c 'echo "deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main" >> /etc/apt/sources.list.d/google.list'
RUN apt-get update
RUN apt-get install -y nodejs firefox google-chrome-stable google-chrome-unstable
RUN npm i -g npm yarn

RUN mkdir /project
ENTRYPOINT ["bash"]
WORKDIR /project
