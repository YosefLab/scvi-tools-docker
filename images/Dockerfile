FROM mambaorg/micromamba:git-4073267-jammy-cuda-11.8.0

ARG MAMBA_DOCKERFILE_ACTIVATE=1

RUN micromamba install --yes --name base \
    python=3.11 --channel conda-forge && \
    micromamba clean --all --yes

RUN micromamba install pytorch torchvision torchaudio pytorch-cuda=11.8 \
    --channel pytorch \
    --channel nvidia \
    --channel conda-forge && \
    micromamba clean --all --yes

RUN pip install --no-cache-dir --upgrade "jax[cuda11_pip]" \
    -f https://storage.googleapis.com/jax-releases/jax_cuda_releases.html

ENV PATH "$MAMBA_ROOT_PREFIX/bin:$PATH"
