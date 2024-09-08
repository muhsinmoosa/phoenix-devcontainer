# Use the official Ubuntu image as the base image
FROM ubuntu:24.04

RUN echo "Acquire::http::Pipeline-Depth 0;" > /etc/apt/apt.conf.d/99custom && \
    echo "Acquire::http::No-Cache true;" >> /etc/apt/apt.conf.d/99custom && \
    echo "Acquire::BrokenProxy    true;" >> /etc/apt/apt.conf.d/99custom

ENV DEBIAN_FRONTEND noninteractive
ENV TZ=UTC
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone


RUN apt-get update && apt-get install -y erlang erlang-dev elixir inotify-tools git zip

RUN mix local.hex --force
RUN mix local.rebar --force
RUN  mix archive.install hex phx_new --force

CMD ["sleep", "infinity"]