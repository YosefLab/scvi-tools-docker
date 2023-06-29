FROM condaforge/mambaforge:latest AS mamba

RUN mamba create --copy -y -p /env \
    python=3.11 -c conda-forge && \
    mamba clean -ayf

RUN mamba install -y -p /env \
    pytorch torchvision torchaudio pytorch-cuda \
    -c pytorch -c nvidia -c conda-forge && \
    mamba clean -ayf

RUN mamba run -p /env \
    python -m pip install --no-cache-dir --upgrade \
    "jax[cuda11_pip]" -f https://storage.googleapis.com/jax-releases/jax_cuda_releases.html && \
    mamba run -p /env \
    python -m pip cache purge

FROM ubuntu:latest

COPY --from=mamba /env /env

ENV PATH "/env/bin:$PATH"
