# Copyright (c) Jupyter Development Team.
# Distributed under the terms of the Modified BSD License.
ARG OWNER=zhushaojun
ARG BASE_CONTAINER=$OWNER/scipy-notebook
FROM $BASE_CONTAINER

LABEL maintainer="Jupyter Project <jupyter@googlegroups.com>"

# Fix DL4006
SHELL ["/bin/bash", "-o", "pipefail", "-c"]

# Install mxnet and autogluon
RUN mamba install --quiet --yes \
    'cudatoolkit=10.2' \
    'python=3.8' && \
    mamba clean --all -f -y && \
    pip install mxnet-cu102==1.7.0 autogluon --no-cache-dir && \
    rm -fr ~/.cache && \
    fix-permissions "${CONDA_DIR}" && \
    fix-permissions "/home/${NB_USER}"
