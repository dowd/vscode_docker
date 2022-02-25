# FROM mcr.microsoft.com/vscode/devcontainers/python:dev-3.8-bullseye
FROM python:3.9-slim-bullseye
ENV CONDA_DIR=/opt/conda
ENV LANG=C.UTF-8 LC_ALL=C.UTF-8
ENV PATH=${CONDA_DIR}/bin:${PATH}


RUN apt-get -y update && \
    apt-get -y install \
    software-properties-common \
    binutils \
    libproj-dev \
    gdal-bin \
    libgdal-dev \
    gcc \
    python3-dev \
    build-essential \
    libxslt-dev \
    libffi-dev \
    libssl-dev \
    libgeos-dev \
    wget \
    git && \
    wget https://github.com/conda-forge/miniforge/releases/latest/download/Miniforge3-Linux-aarch64.sh -O /tmp/miniforge.sh && \
    /bin/bash /tmp/miniforge.sh -b -p ${CONDA_DIR}

# Create the environment:
COPY environment.yml .
RUN conda env create -f environment.yml
RUN conda init

ARG conda_env=geo2

#ENV PATH /opt/conda/envs/$conda_env/bin:$PATH
#RUN /bin/bash -c "source activate $conda_env"
ENTRYPOINT /bin/bash -c "conda activate $conda_env"
