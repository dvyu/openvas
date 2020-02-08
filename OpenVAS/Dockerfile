FROM debian
MAINTAINER Yuri Dvin <dvyu@yandex.ru>

RUN apt-get update && apt-get install -y telnet procps net-tools htop iputils-ping vim curl zip git gcc pkg-config libssh-gcrypt-dev libgnutls28-dev libglib2.0-dev libpcap-dev libgpgme-dev bison libksba-dev libsnmp-dev libgcrypt20-dev libhiredis0.14 cmake libgpgme11-dev uuid-dev libldap2-dev libhiredis-dev libxml++2.6-dev

RUN git clone https://github.com/greenbone/gvm-libs.git
RUN cd gvm-libs
RUN git checkout gvm-libs-11.0
RUN cmake .
RUN make
RUN make install
RUN cd /
RUN git clone https://github.com/greenbone/openvas.git
RUN git checkout openvas-7.0
RUN cd openvas
RUN cmake .
RUN make
RUN make install

#ln -s /usr/local/lib/libopenvas_nasl.so.11 /usr/lib/libopenvas_nasl.so.11
#ln -s /usr/local/lib/libgvm_base.so.11 /usr/lib/libgvm_base.so.11
#ln -s /usr/local/lib/libopenvas_misc.so.11 /usr/lib/libopenvas_misc.so.11
#ln -s /usr/local/lib/libgvm_util.so.11 /usr/lib/libgvm_util.so.11

ADD docker-entrypoint.sh /
RUN chmod +x /docker-entrypoint.sh
ENTRYPOINT ["/docker-entrypoint.sh"]
