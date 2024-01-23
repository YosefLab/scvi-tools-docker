FROM condaforge/mambaforge:latest AS mamba

ARG PYTHON_VERSION=3.11
RUN mamba create --copy -y -p /env \
    python=${PYTHON_VERSION} -c conda-forge && \
    mamba clean -ayf

ARG CUDA_VERSION=11
RUN mamba install -y -p /env \
    cudnn cudatoolkit cuda-nvcc=${CUDA_VERSION} \
    -c anaconda -c nvidia && \
    mamba clean -ayf

ARG CUDA_VERSION=11
RUN mamba install -y -p /env \
    jaxlib=*=*cuda* jax pytorch torchvision torchaudio pytorch-cuda=${CUDA_VERSION} \
    -c pytorch -c nvidia -c conda-forge && \
    mamba clean -ayf

RUN mamba install -y -p /env \
    git -c anaconda && \
    mamba clean -ayf

RUN mamba install -y -p /env \
    gcc cxx-compiler -c conda-forge && \
    mamba clean -ayf

FROM ubuntu:latest

COPY --from=mamba /env /env

ENV PATH "/env/bin:$PATH"
