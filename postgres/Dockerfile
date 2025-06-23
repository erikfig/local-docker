FROM postgres:latest

RUN apt-get update && apt-get install -y postgresql-server-dev-15 build-essential git && \
    sed -i '/en_US.UTF-8/s/^# //' /etc/locale.gen && \
    locale-gen

ENV LANG=en_US.UTF-8
ENV LANGUAGE=en_US:en
ENV LC_ALL=en_US.UTF-8

RUN git clone --branch v0.5.1 https://github.com/pgvector/pgvector.git && \
    cd pgvector && make && make install
