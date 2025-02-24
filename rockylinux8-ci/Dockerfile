FROM rockylinux:8

LABEL maintainer="vladimir.antropov@milaboratories.com"

RUN dnf -y install dnf-plugins-core \
    && dnf -y groupinstall "Development Tools" \
    && dnf config-manager --set-enabled powertools \
    && dnf -y install epel-release \
    && dnf -y install zlib-devel bzip2-devel lz4-devel snappy-devel \
    libzstd-devel liburing-devel tbb-devel jq unzip zip curl wget \
    patchelf cmake

RUN curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip" \
    && unzip awscliv2.zip \
    && ./aws/install \
    && rm -rf awscliv2.zip ./aws

RUN dnf clean all \
    && rm -rf /var/cache/dnf	

CMD ["/bin/bash"]
