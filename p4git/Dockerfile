FROM ubuntu:trusty

MAINTAINER Anoop Vijayan Maniankara

RUN apt-get install -y wget && \
    wget -q http://package.perforce.com/perforce.pubkey -O- | sudo apt-key add - &&\
    echo 'deb http://package.perforce.com/apt/ubuntu trusty release'>/etc/apt/sources.list.d/perforce.sources.list && \
    apt-get update && \
    apt-get install -y helix-git-fusion

CMD ["tail", "-f", "/dev/null"]
