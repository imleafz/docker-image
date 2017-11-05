FROM ubuntu:latest

ARG TZ="Asia/Shanghai"

ENV TZ ${TZ} 
ENV SERVIER_VERSION=1.4.125 

RUN apt update \
    && apt install tzdata axel python libsdl2-2.0-0 \
    && axel -qn 20 http://www.files.froemling.net/bombsquad/builds/BombSquad_Server_Linux_64bit_${SERVER_VERSION}.tar.gz
    && tar -xzf BombSquad_*.tar.gz \
    && mv BombSquad_Server_Linux_64bit_${SERVER_VERSION} BombSquad \
    && ln -sf /usr/share/zoneinfo/${TZ} /etc/localtime \
    && echo ${TZ} > /etc/timezone \
    && rm -rf BombSquad_*.tar.gz

WORKDIR /BombSquad

EXPOSE 43210/udp

CMD ["./bombsquad_server"]
