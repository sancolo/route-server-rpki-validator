
FROM debian:stable

EXPOSE 179

RUN apt-get update && apt-get install -y \
        autoconf \
	bison \
	build-essential \
	curl \
	flex \
	libreadline-dev \
	libncurses5-dev \
	m4 \
	unzip \
	libssh-dev \
	procps \
	net-tools \
	tree \
	lsof

WORKDIR /root
RUN curl -O -L https://github.com/BIRD/bird/archive/v2.0.1.zip
RUN unzip v2.0.1.zip

# Este directorio debe ser montado como un volumen local con la opcion de comando de docker `-v $HOME/rbird1:/etc/bird:rw'.
# El archivo en el host $HOME/rbird1/bird.conf es usado como el archivo de configuracion para BIRD.
RUN mkdir /etc/bird

RUN cd bird-2.0.1 && \
	autoreconf && \
	./configure --enable-libssh && \
	make && \
	make install

CMD bird -c /etc/bird/bird.conf -d
