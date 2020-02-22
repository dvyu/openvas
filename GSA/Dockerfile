FROM debian
MAINTAINER Yuri Dvin <dvyu@yandex.ru>

RUN apt-get update && apt-get install -y telnet procps net-tools htop iputils-ping vim curl zip git pkg-config libssh-gcrypt-dev libmicrohttpd-dev libglib2.0-dev libxml2-dev apt-transport-https libhiredis0.14 libhiredis-dev cmake libgpgme11-dev gnupg2 gettext python-polib

RUN curl --silent --show-error https://dl.yarnpkg.com/debian/pubkey.gpg | apt-key add -
RUN echo "deb https://dl.yarnpkg.com/debian/ stable main" | tee /etc/apt/sources.list.d/yarn.list
RUN curl --silent --show-error https://deb.nodesource.com/gpgkey/nodesource.gpg.key | apt-key add -
RUN echo "deb https://deb.nodesource.com/node_8.x stretch main" | tee /etc/apt/sources.list.d/nodesource.list

RUN apt-get update && apt-get install -y nodejs yarn

RUN cd / && git clone https://github.com/greenbone/gvm-libs.git && cd gvm-libs && git checkout tags/v11.0.0 && cmake . && make && make install
RUN cd / && git clone https://github.com/greenbone/gsa.git && cd gsa && git checkout tags/v9.0.0 && cmake . && make && make install

RUN ln -s /usr/local/lib/libgvm_base.so.11 /usr/lib/libgvm_base.so.11 && ln -s /usr/local/lib/libgvm_util.so.11 /usr/lib/libgvm_util.so.11 && ln -s /usr/local/lib/libgvm_gmp.so.11 /usr/lib/libgvm_gmp.so.11

ADD docker-entrypoint.sh /
RUN chmod +x /docker-entrypoint.sh
ENTRYPOINT ["/docker-entrypoint.sh"]
