ARG BASE_CONTAINER=quay.io/jupyter/pytorch-notebook:2025-03-14

FROM $BASE_CONTAINER

ENV KERNEL_LANGUAGE python

ADD jupyter_enterprise_gateway_kernel_image_files*.tar.gz /usr/local/bin/

RUN conda install --quiet --yes \
    pillow \
    future \
    pycryptodomex && \
    fix-permissions $CONDA_DIR

USER root

RUN chown jovyan:users /usr/local/bin/bootstrap-kernel.sh && \
	chmod 0755 /usr/local/bin/bootstrap-kernel.sh && \
	chown -R jovyan:users /usr/local/bin/kernel-launchers

USER jovyan

# Disble healthcheck inherited from notebook image
HEALTHCHECK NONE

CMD [ "/usr/local/bin/bootstrap-kernel.sh" ]
