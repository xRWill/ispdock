FROM  ubuntu

RUN apt-get update && apt-get -y install lsb-release gnupg wget &&\
  wget -O- https://repo.nperf.com/apt/conf/nperf-server.gpg.key | gpg --dearmor > /usr/share/keyrings/nperf-archive-keyring.gpg &&\
  echo "deb [arch=amd64 signed-by=/usr/share/keyrings/nperf-archive-keyring.gpg] https://repo.nperf.com/apt $(lsb_release -sc) main non-free" >> /etc/apt/sources.list.d/nperf.list &&\
  apt-get update &&\
  apt-get -y install nperf-server

COPY  nperf-server.conf   /etc/nperf/nperf-server.conf

EXPOSE 8080
EXPOSE 8443

CMD /usr/bin/nPerfServer -x --pidfile=/var/lib/nperf-server/nPerfServer.pid -p 8080 -t 8443 --uuidfile=/var/lib/nperf-server/nPerfServer.uuid
