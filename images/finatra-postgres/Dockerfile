FROM buildpack-deps:bionic

ENV CI True

# Docker prereq
ENV TZ=Etc/UTC
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone
RUN apt-get update

# Postgres repo
RUN echo "deb http://apt.postgresql.org/pub/repos/apt/ bionic-pgdg main" >> /etc/apt/sources.list.d/pgdg.list
RUN curl -fsSL https://www.postgresql.org/media/keys/ACCC4CF8.asc  | apt-key add -

RUN apt-get update
RUN apt-get install -y apt-transport-https ca-certificates curl software-properties-common awscli
RUN apt-get install -y openjdk-8-jdk
RUN apt-get install -y postgresql-9.6 postgresql-contrib-9.6

RUN update-rc.d postgresql enable
RUN service postgresql start

USER postgres
RUN psql --command "CREATE USER adazza WITH SUPERUSER PASSWORD 'adazza';"
RUN echo "host all  all    0.0.0.0/0  md5" >> /etc/postgresql/9.6/main/pg_hba.conf
RUN echo "listen_addresses='*'" >> /etc/postgresql/9.6/main/postgresql.conf

USER root

RUN mkdir /project
ENTRYPOINT ["bash"]
WORKDIR /project
