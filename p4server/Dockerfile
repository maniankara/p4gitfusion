FROM oraclelinux:6

MAINTAINER Anoop Vijayan Maniankara

ENV P4ROOTPW p4gitfusion
ENV P4PORT p4server:1666
ENV P4USER perforce

COPY perforce.repo /etc/yum.repos.d/

RUN echo $(grep $(hostname) /etc/hosts | cut -f1) p4server >> /etc/hosts && \
    rpm --import http://package.perforce.com/perforce.pubkey && \
    yum install -y perforce-server && \
    p4d -d && \
    p4 -u perforce protect -o && \
    p4 passwd -P $P4ROOTPW $P4USER 

RUN echo $(grep $(hostname) /etc/hosts | cut -f1) p4server >> /etc/hosts && \
    yum install -y helix-git-fusion-trigger && \
    p4d -d 
#    /opt/perforce/git-fusion/libexec/p4gf_submit_trigger.py --install  $P4PORT $P4USER $P4ROOTPW
 

CMD ["p4d"]
