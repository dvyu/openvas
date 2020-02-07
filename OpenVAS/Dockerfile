FROM debian
MAINTAINER Yuri Dvin <dvyu@yandex.ru>

RUN apt-get update && apt-get install -y telnet procps net-tools htop iputils-ping vim curl zip git gcc pkg-config libssh-gcrypt-dev libgnutls28-dev libglib2.0-dev libpcap-dev libgpgme-dev bison libksba-dev libsnmp-dev libgcrypt20-dev cmake libhiredis0.14

#apt-get install     cmake     pkg-config     libglib2.0-dev     libgpgme11-dev     libgnutls28-dev     uuid-dev     libssh-gcrypt-dev     libldap2-dev     libhiredis-dev libxml++2.6-dev

#apt-get install gcc pkg-config libssh-gcrypt-dev libgnutls28-dev \
#libglib2.0-dev libpcap-dev libgpgme-dev bison libksba-dev libsnmp-dev \
#libgcrypt20-dev redis-server

RUN git clone https://github.com/greenbone/gvm-libs.git
RUN git checkout gvm-libs-11.0
RUN git clone https://github.com/greenbone/openvas.git
RUN git checkout openvas-7.0
RUN cd openvas
RUN cmake .

ADD reload /
RUN chmod +x /reload

ADD docker-entrypoint.sh /
RUN chmod +x /docker-entrypoint.sh
ENTRYPOINT ["/docker-entrypoint.sh"]ii
