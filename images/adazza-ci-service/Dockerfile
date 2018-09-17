FROM buildpack-deps:bionic

ENV CI True

# Docker prereq
ENV TZ=Etc/UTC
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone
RUN apt-get update
RUN apt-get install -y apt-transport-https ca-certificates curl software-properties-common awscli zip
RUN apt-get install -y openjdk-8-jdk

# Install OS deps
RUN mkdir /project
ENTRYPOINT ["bash"]
WORKDIR /project
