FROM phusion/baseimage:0.10.2 as builder
LABEL maintainer="13088966264@163.com"
LABEL description="编译Substrate的Docker镜像"

ENV DEBIAN_FRONTEND=noninteractive
ENV PATH=/substrate/bin:/root/.cargo/bin:$PATH
ENV TERM=xterm

RUN apt-get update && \
	apt-get dist-upgrade -y -o Dpkg::Options::="--force-confold" && \
	apt-get install -y cmake pkg-config libssl-dev git gcc build-essential clang libclang-dev

RUN curl https://sh.rustup.rs -sSf | sh -s -- -y && \
	# rustup toolchain install nightly && \
	rustup update nightly && \
	rustup target add wasm32-unknown-unknown --toolchain nightly && \
	rustup default stable && \
	cargo install --git https://github.com/paritytech/cargo-contract cargo-contract --force && \
	rm -rf ~/.cargo/git/* && \
	rm -rf ~/.cargo/registry/*
