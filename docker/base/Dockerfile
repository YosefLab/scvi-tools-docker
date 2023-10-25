FROM condaforge/mambaforge:latest AS mamba

ARG PYTHON_VERSION=3.11
RUN mamba create --copy -y -p /env \
    python=${PYTHON_VERSION} -c conda-forge && \
    mamba clean -ayf

ARG CUDA_VERSION=11
RUN mamba install -y -p /env \
    pytorch torchvision torchaudio pytorch-cuda=${CUDA_VERSION} cuda-nvcc=${CUDA_VERSION} \
    -c pytorch -c nvidia -c conda-forge && \
    mamba clean -ayf

ARG CUDA_VERSION=11
RUN mamba run -p /env \
    python -m pip install --no-cache-dir --upgrade \
    jax[cuda${CUDA_VERSION}_pip] -f https://storage.googleapis.com/jax-releases/jax_cuda_releases.html && \
    mamba run -p /env \
    python -m pip cache purge

RUN mamba install -y -p /env \
    git -c anaconda && \
    mamba clean -ayf

RUN mamba install -y -p /env \
    gcc -c conda-forge && \
    mamba clean -ayf

FROM ubuntu:latest

COPY --from=mamba /env /env

ENV PATH "/env/bin:$PATH"
