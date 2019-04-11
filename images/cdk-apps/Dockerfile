FROM buildpack-deps:bionic

ENV CI True

# Docker prereq
ENV TZ=Etc/UTC
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone
RUN apt-get update
RUN apt-get install -y apt-transport-https ca-certificates curl software-properties-common awscli
RUN curl -fsSL https://download.docker.com/linux/ubuntu/gpg | apt-key add -
RUN add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"

# Postgres repo
RUN echo "deb http://apt.postgresql.org/pub/repos/apt/ bionic-pgdg main" >> /etc/apt/sources.list.d/pgdg.list
RUN curl -fsSL https://www.postgresql.org/media/keys/ACCC4CF8.asc  | apt-key add -

# Node prereq
RUN curl -sL https://deb.nodesource.com/setup_10.x | bash -

# Postgres repo
RUN echo "deb http://apt.postgresql.org/pub/repos/apt/ bionic-pgdg main" >> /etc/apt/sources.list.d/pgdg.list
RUN curl -fsSL https://www.postgresql.org/media/keys/ACCC4CF8.asc  | apt-key add -

# Run Update after settting up required repositories.
RUN apt-get update

RUN apt-get install -y openjdk-8-jdk
RUN apt-get install -y postgresql-9.6 postgresql-contrib-9.6

RUN update-rc.d postgresql enable

USER postgres
RUN service postgresql start && psql --command "CREATE USER adazza_test_user WITH SUPERUSER PASSWORD 'adazza_test_user';"
RUN echo "host all  all    0.0.0.0/0  md5" >> /etc/postgresql/9.6/main/pg_hba.conf
RUN echo "listen_addresses='*'" >> /etc/postgresql/9.6/main/postgresql.conf

USER root

RUN apt-get install -y nodejs docker-ce awscli

# Versioned deps
RUN npm i -g npm@'~6.9.0' yarn@'1.15.2' n@'3.0.2'
RUN n 10.15.3

RUN mkdir /project
ENTRYPOINT ["bash"]
WORKDIR /project
