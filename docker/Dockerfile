FROM condaforge/miniforge3:latest AS conda

ARG PYTHON_VERSION=3.11
RUN mamba create --copy -y -p /env \
    python=${PYTHON_VERSION} -c conda-forge && \
    mamba clean -ayf

ARG CUDA_VERSION=11
RUN CONDA_OVERRIDE_CUDA=${CUDA_VERSION} mamba install -y -p /env \
    pytorch torchvision torchaudio pytorch-cuda=${CUDA_VERSION} \
    jaxlib=*=*cuda* jax cuda-nvcc -c pytorch -c conda-forge -c nvidia && \
    mamba clean -ayf

RUN mamba install -y -p /env \
    git -c anaconda && \
    mamba clean -ayf

RUN mamba install -y -p /env \
    gcc cxx-compiler -c conda-forge && \
    mamba clean -ayf

FROM ubuntu:latest AS cuda
COPY --from=conda /env /env
ENV PATH "/env/bin:$PATH"

ARG PYTHON_VERSION=3.11
ARG CUDA_VERSION=11
FROM scverse/scvi-tools:py${PYTHON_VERSION}-cu${CUDA_VERSION}-base AS base

FROM base AS latest
ARG DEPENDENCIES=""
RUN pip install --no-cache-dir "scvi-tools[${DEPENDENCIES}] @ git+https://github.com/scverse/scvi-tools" && \
    pip cache purge

FROM base AS stable
ARG DEPENDENCIES=""
RUN pip install -U --no-cache-dir "scvi-tools[${DEPENDENCIES}]" && \
    pip cache purge

FROM base AS branch
ARG SCVI_TOOLS_VERSION=main
ARG DEPENDENCIES=""
RUN pip install --no-cache-dir "scvi-tools[${DEPENDENCIES}] @ git+https://github.com/scverse/scvi-tools@${SCVI_TOOLS_VERSION}" && \
    pip cache purge

FROM base AS semver
ARG SCVI_TOOLS_VERSION=latest
ARG DEPENDENCIES=""
RUN pip install --no-cache-dir "scvi-tools[${DEPENDENCIES}]==${SCVI_TOOLS_VERSION}" && \
    pip cache purge
