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
RUN apt-get install -y unzip
RUN apt-get install -y python-pip
RUN pip install ansible==2.6.3
RUN pip install boto3 boto botocore
RUN pip install dnspython

RUN wget --quiet https://releases.hashicorp.com/packer/1.3.2/packer_1.3.2_linux_amd64.zip -O /tmp/packer.zip
RUN unzip /tmp/packer.zip -d /usr/local/bin/
RUN chmod '0755' /usr/local/bin/packer
RUN rm /tmp/packer.zip

RUN update-rc.d postgresql enable

USER postgres
RUN service postgresql start && psql --command "CREATE USER adazza_test_user WITH SUPERUSER PASSWORD 'adazza_test_user';"
RUN echo "host all  all    0.0.0.0/0  md5" >> /etc/postgresql/9.6/main/pg_hba.conf
RUN echo "listen_addresses='*'" >> /etc/postgresql/9.6/main/postgresql.conf

USER root

RUN mkdir /project
ENTRYPOINT ["bash"]
WORKDIR /project
