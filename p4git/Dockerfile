FROM ubuntu:trusty

MAINTAINER Anoop Vijayan Maniankara

ENV GITPASS p4gitfusion && \
    P4PORT p4server:1666

RUN apt-get install -y wget && \
    wget -q http://package.perforce.com/perforce.pubkey -O- | sudo apt-key add - &&\
    echo 'deb http://package.perforce.com/apt/ubuntu trusty release'>/etc/apt/sources.list.d/perforce.sources.list && \
    apt-get update && \
    apt-get install -y helix-git-fusion perforce-server && \
    echo "$GITPASS\n$GITPASS" | passwd git 

RUN /opt/perforce/git-fusion/libexec/configure-git-fusion.sh --server remote --super perforce --superpassword p4gitfusion --p4port p4server:1666 --gfp4password p4gitfusion --timezone UTC --unknownuser pusher --https no -n


CMD ["tail", "-f", "/dev/null"]
