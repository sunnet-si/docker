# "ported" by Adam Miller <maxamillion@fedoraproject.org> from
#   https://github.com/fedora-cloud/Fedora-Dockerfiles
#
# Originally written for Fedora-Dockerfiles by
#   scollier <scollier@redhat.com>

FROM centos:centos6
MAINTAINER Olof <olof.astrand@gmail.com>

RUN yum -y update; yum clean all
RUN yum groupinstall "Development Tools" -y  && \
  yum install imake libxml2-devel motif-devel libsmi-devel openssh-server passwd -y && \
  yum install libXt-devel rpm-build cmake tar rsync createrepo systemtap csh emacs openssh-server ksh -y && \
  yum clean all

ADD ./start.sh /start.sh
RUN mkdir /var/run/sshd

RUN ssh-keygen -t rsa -f /etc/ssh/ssh_host_rsa_key -N '' 

RUN chmod 755 /start.sh
# EXPOSE 22
RUN ./start.sh


RUN mkdir -p /home/src

ENV compiler GNU
ENV PLATFORM LINUX
ENV LINK_WITH_SNMP "yes"

VOLUME /home/src

WORKDIR /home/src

CMD ["/usr/sbin/sshd", "-D", "-e"]
