FROM buildpack-deps:bionic

ENV CI True

# Docker prereq
ENV TZ=Etc/UTC
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone
RUN apt-get update
RUN apt-get install -y apt-transport-https ca-certificates curl software-properties-common awscli
RUN apt-get install -y openjdk-8-jdk
RUN apt-get install -y postgresql postgresql-contrib


USER postgres
RUN /etc/init.d/postgresql start &&\
    psql --command "CREATE USER adazza WITH SUPERUSER PASSWORD 'adazza';"
RUN echo "host all  all    0.0.0.0/0  md5" >> /etc/postgresql/10/main/pg_hba.conf
RUN echo "listen_addresses='*'" >> /etc/postgresql/10/main/postgresql.conf

USER root

EXPOSE 5432

# Install OS deps
RUN apt-get update

RUN mkdir /project
ENTRYPOINT ["bash"]
WORKDIR /project
