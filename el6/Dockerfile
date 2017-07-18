FROM centos:centos6

RUN yum -y install epel-release && yum clean all && \
    yum -y install \
    gcc \
    make \
    rpmdevtools \
    mock \
    perl \
    sudo \
    tar \
    zlib-devel \
    createrepo \
    wget

RUN adduser \
    --comment "RPM Builder" \
    --home /home/rpm-builder \
    --create-home \
    rpm-builder

ENV RHEL_VERSION 6
USER rpm-builder
RUN rpmdev-setuptree
WORKDIR /home/rpm-builder
CMD /bin/bash
