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
    jaxlib=*=*cuda* jax cuda pytorch torchvision torchaudio pytorch-cuda=${CUDA_VERSION} \
    -c pytorch -c nvidia -c conda-forge && \
    mamba clean -ayf

RUN mamba install -y -p /env \
    git -c anaconda && \
    mamba clean -ayf

RUN mamba install -y -p /env \
    gcc cxx-compiler -c conda-forge && \
    mamba clean -ayf

FROM ubuntu:latest AS cuda
COPY --from=mamba /env /env
ENV PATH "/env/bin:$PATH"

ARG PYTHON_VERSION=3.11
ARG CUDA_VERSION=11
ENV PYTHON_VERSION=${PYTHON_VERSION}
ENV CUDA_VERSION=${CUDA_VERSION}
FROM scverse/scvi-tools:py${PYTHON_VERSION}-cu${CUDA_VERSION}-base AS base

FROM base AS latest
ARG DEPENDENCIES=""
ENV DEPENDENCIES=${DEPENDENCIES}
RUN pip install --no-cache-dir "scvi-tools[${DEPENDENCIES}] @ git+https://github.com/scverse/scvi-tools" && \
    pip cache purge

FROM base AS stable
ARG DEPENDENCIES=""
ENV DEPENDENCIES=${DEPENDENCIES}
RUN pip install -U --no-cache-dir "scvi-tools[${DEPENDENCIES}]" && \
    pip cache purge

FROM base AS branch
ARG SCVI_TOOLS_VERSION=main
ARG DEPENDENCIES=""
ENV SCVI_TOOLS_VERSION=${SCVI_TOOLS_VERSION}
ENV DEPENDENCIES=${DEPENDENCIES}
RUN pip install --no-cache-dir "scvi-tools[${DEPENDENCIES}] @ git+https://github.com/scverse/scvi-tools@${SCVI_TOOLS_VERSION}" && \
    pip cache purge

FROM base AS semver
ARG SCVI_TOOLS_VERSION=latest
ARG DEPENDENCIES=""
ENV SCVI_TOOLS_VERSION=${SCVI_TOOLS_VERSION}
ENV DEPENDENCIES=${DEPENDENCIES}
RUN pip install --no-cache-dir "scvi-tools[${DEPENDENCIES}]==${SCVI_TOOLS_VERSION}" && \
    pip cache purge
