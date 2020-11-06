FROM ubuntu:latest AS intermedier

RUN apt-get update

RUN apt-get install git -y

RUN git clone https://github.com/Mehdi13k8/timemanager_2020_35.git

FROM elixir:latest

RUN mix local.hex --force

RUN mix local.rebar --force

RUN wget https://github.com/phoenixframework/archives/raw/master/phoenix_new.ez

RUN mix archive.install ./phoenix_new.ez --force

COPY --from=intermedier /timemanager_2020_35/timemanager-api ./timemanager-api

WORKDIR /timemanager-api

RUN mix deps.get --force

RUN curl -sL https://deb.nodesource.com/setup_12.x | bash -

RUN apt-get install -y -q nodejs

RUN apt install make -y

RUN apt-get install build-essential -y

RUN apt-get update && apt-get install -y \
    inotify-tools \
    && rm -rf /var/lib/apt/lists/*
