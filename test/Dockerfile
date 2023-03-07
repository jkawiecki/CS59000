FROM nvidia/cuda:11.8.0-base-ubuntu22.04

RUN \
	apt-get update && \
	apt-get -y upgrade && \
	apt install -y \
		wget build-essential zlib1g-dev libncurses5-dev libgdbm-dev libnss3-dev libssl-dev libsqlite3-dev libreadline-dev libffi-dev libbz2-dev liblzma-dev && \
	apt clean && \
	rm -rf /var/lib/apt/lists/*

WORKDIR /temp

RUN wget https://www.python.org/ftp/python/3.7.5/Python-3.7.5.tgz && \
    tar -xzf Python-3.7.5.tgz

RUN cd Python-3.7.5 && \
    ./configure --enable-optimizations && \
    make && \
    make install

WORKDIR /workspace

RUN rm -r /temp && \
    ln -s /usr/local/bin/python3 /usr/local/bin/python && \
    ln -s /usr/local/bin/pip3 /usr/local/bin/pip

RUN \
	apt-get update && \
	apt-get -y upgrade && \
	apt-get install -y gcc git sudo unzip vim && \
	apt-get install -y libopenmpi-dev

WORKDIR /app
