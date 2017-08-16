FROM centos:centos7

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

# sudo config
RUN sed -i -e 's/Defaults    env_reset/#Defaults    env_reset/' /etc/sudoers \
    && sed -i -e 's/Defaults    secure_path/#Defaults    secure_path/' /etc/sudoers \
    && echo 'Defaults    env_keep += "PATH"' >> /etc/sudoers \
    && echo 'rpm-builder    ALL=(ALL) NOPASSWD:ALL' >> /etc/sudoers

ENV RHEL_VERSION 7
USER rpm-builder
RUN rpmdev-setuptree
WORKDIR /home/rpm-builder
CMD /bin/bash

