FROM debian
MAINTAINER Yuri Dvin <dvyu@yandex.ru>

RUN apt-get update && apt-get install -y telnet procps net-tools htop iputils-ping vim curl zip git gcc pkg-config libssh-gcrypt-dev libgnutls28-dev libglib2.0-dev libpcap-dev libgpgme-dev bison libksba-dev libsnmp-dev libgcrypt20-dev

#apt-get install gcc pkg-config libssh-gcrypt-dev libgnutls28-dev \
#libglib2.0-dev libpcap-dev libgpgme-dev bison libksba-dev libsnmp-dev \
#libgcrypt20-dev redis-server

ADD reload /
RUN chmod +x /reload

ADD docker-entrypoint.sh /
RUN chmod +x /docker-entrypoint.sh
ENTRYPOINT ["/docker-entrypoint.sh"]ii
