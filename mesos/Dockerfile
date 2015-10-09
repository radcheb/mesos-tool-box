FROM centos:centos6

MAINTAINER Radhwane CHEBAANE, r.chebaane@mindlytix.com

ENV VERSION 0.24.1
ENV PKG_RELEASE 0.2.35

RUN yum update -y

RUN yum install -y tar wget which

# Import the CERN GPG key.
RUN rpm --import http://linuxsoft.cern.ch/cern/centos/7/os/x86_64/RPM-GPG-KEY-cern

 # Fetch the Apache Maven repo file.
RUN wget http://repos.fedorapeople.org/repos/dchen/apache-maven/epel-apache-maven.repo -O /etc/yum.repos.d/epel-apache-maven.repo

# Install essential development tools.
RUN yum groupinstall -y "Development Tools"

RUN wget -O /etc/yum.repos.d/slc6-devtoolset.repo http://linuxsoft.cern.ch/cern/devtoolset/slc6-devtoolset.repo

RUN yum update -y

RUN yum install -y devtoolset-2-toolchain

RUN yum install -y apache-maven python-devel java-1.7.0-openjdk-devel zlib-devel libcurl-devel openssl-devel cyrus-sasl-devel cyrus-sasl-md5 apr-devel subversion-devel apr-util-devel

RUN yum install -y curl && \ 
  curl -s -O http://downloads.mesosphere.io/master/centos/6/mesos-${VERSION}-${PKG_RELEASE}.centos65.x86_64.rpm && \
  rpm -Uvh mesos-${VERSION}-${PKG_RELEASE}.centos65.x86_64.rpm && \
  rm mesos-${VERSION}-${PKG_RELEASE}.centos65.x86_64.rpm