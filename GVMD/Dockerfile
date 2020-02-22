FROM debian
MAINTAINER Yuri Dvin <dvyu@yandex.ru>

RUN apt-get update && apt-get install -y telnet procps net-tools htop iputils-ping vim curl zip git pkg-config libssh-gcrypt-dev libgnutls28-dev libhiredis-dev libxml2-dev cmake libgpgme11-dev gnupg2 libglib2.0-dev libical-dev postgresql-server-dev-all

#RUN cd / && git clone https://github.com/greenbone/gvm-libs.git && cd gvm-libs && git checkout tags/v11.0.0 && cmake . && make && make install
RUN cd / && git clone https://github.com/greenbone/gvm-libs.git && cd gvm-libs && git checkout gvm-libs-11.0 && cmake . && make && make install
RUN cd / && git clone https://github.com/greenbone/gvmd.git && cd gvmd && git checkout gvmd-9.0 && cmake . && make && make install

ADD docker-entrypoint.sh /
RUN chmod +x /docker-entrypoint.sh
ENTRYPOINT ["/docker-entrypoint.sh"]
