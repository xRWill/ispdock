FROM  ubuntu AS prepare

RUN apt-get update && apt-get -y install wget systemd
CMD systemd

FROM prepare
RUN wget -O- https://static.minhaconexao.com.br/mc-server-scripts/3.0.5/install-x86_64.sh | bash

EXPOSE 9090

CMD mc-test --cert-path /etc/mc-test/keys/star.mcservers.co.crt --pfx-path /etc/mc-test/keys/full-cert.pfx --port 9090
