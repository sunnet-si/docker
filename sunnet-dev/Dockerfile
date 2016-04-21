FROM centos:7

MAINTAINER Olof "olof.astrand@gmail.com"

RUN yum install epel-release -y
#RUN yum update -y
#  yum groupinstall "X Software Development" -y  && \


RUN yum groupinstall "Development Tools" -y  && \
  yum install imake libxml2-devel motif-devel libsmi-devel -y && \
  yum install libXt-devel rpm-build cmake tar rsync createrepo systemtap csh emacs openssh-server -y && \
  yum clean all


RUN mkdir -p /home/src

ENV compiler GNU
ENV PLATFORM LINUX
ENV LINK_WITH_SNMP "yes"

VOLUME /home/src

WORKDIR /home/src

CMD ["/usr/sbin/sshd", "-D", "-e"]

# tigervnc-server 
#RUN curl --silent --location https://rpm.nodesource.com/setup_4.x | bash -
#RUN yum install nodejs -y
#RUN yum clean all
