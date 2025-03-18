# Ubuntu:xenial
ARG BASE_CONTAINER=quay.io/jupyter/pytorch-notebook:cuda11-2025-03-14
FROM $BASE_CONTAINER

ENV DEBIAN_FRONTEND=noninteractive

USER root

RUN apt-get update && apt-get install -yq \
    build-essential \
    libsm6 \
    libxext-dev \
    libxrender1 \
    python3-dev \
    tzdata \
    unzip && \
    rm -rf /var/lib/apt/lists/* && \
    pip install --upgrade future pycryptodomex ipykernel

ADD jupyter_enterprise_gateway_kernel_image_files*.tar.gz /usr/local/bin/


RUN chown jovyan:users /usr/local/bin/bootstrap-kernel.sh && \
    chmod 0755 /usr/local/bin/bootstrap-kernel.sh && \
    chown -R jovyan:users /usr/local/bin/kernel-launchers


USER jovyan
ENV KERNEL_LANGUAGE python
CMD /usr/local/bin/bootstrap-kernel.sh
