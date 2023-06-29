ARG ubuntu_version=latest
ARG mamba_version=latest
ARG python_version=3.11
ARG cuda_version=11

FROM condaforge/mambaforge:$mamba_version AS mamba

RUN mamba create --copy -y -p /env \
    python=$python_version -c conda-forge && \
    mamba clean -ayf

RUN mamba install -y -p /env \
    pytorch torchvision torchaudio pytorch-cuda=$cuda_version \
    -c pytorch -c nvidia -c conda-forge && \
    mamba clean -ayf

RUN mamba run -p /env \
    python -m pip install --no-cache-dir --upgrade \
    jax[cuda$cuda_version_pip] -f https://storage.googleapis.com/jax-releases/jax_cuda_releases.html && \
    mamba run -p /env \
    python -m pip cache purge

FROM ubuntu:${ubuntu_version}

COPY --from=mamba /env /env

ENV PATH "/env/bin:$PATH"
