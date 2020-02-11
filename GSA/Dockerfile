FROM debian
MAINTAINER Yuri Dvin <dvyu@yandex.ru>

RUN apt-get update && apt-get install -y telnet procps net-tools htop iputils-ping vim curl zip git libmicrohttpd-dev libxml2-dev apt-transport-https 

RUN curl --silent --show-error https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -
RUN echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list
RUN curl --silent --show-error https://deb.nodesource.com/gpgkey/nodesource.gpg.key | sudo apt-key add -
RUN echo "deb https://deb.nodesource.com/node_8.x stretch main" | sudo tee /etc/apt/sources.list.d/nodesource.list

RUN apt-get update && apt-get install -y nodejs yarn

RUN cd / && git clone https://github.com/greenbone/gsa.git && cd gsa && git checkout tags/v9.0.0 && cmake . && make && make install

ADD docker-entrypoint.sh /
RUN chmod +x /docker-entrypoint.sh
ENTRYPOINT ["/docker-entrypoint.sh"]
