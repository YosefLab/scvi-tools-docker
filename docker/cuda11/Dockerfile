FROM condaforge/miniforge3:latest AS base

RUN head -n -1 "${HOME}/.bashrc" > "${HOME}/tmp.bashrc" ; \
    mv "${HOME}/tmp.bashrc" "${HOME}/.bashrc"

ARG PYTHON_VERSION
RUN mamba create --copy -y -p /env \
    python=${PYTHON_VERSION} -c conda-forge && \
    mamba clean -ayf

RUN mamba install -y -p /env \
    gcc cxx-compiler -c conda-forge && \
    mamba clean -ayf

ARG CUDA_VERSION=11
RUN CONDA_OVERRIDE_CUDA=${CUDA_VERSION} mamba install -y -p /env \
    pytorch torchvision torchaudio pytorch-cuda=${CUDA_VERSION} \
    -c pytorch -c nvidia && \
    mamba clean -ayf

ARG CUDA_VERSION=11
RUN mamba run -p /env \
    python -m pip install --no-cache-dir -U "jax[cuda${CUDA_VERSION}_pip]" \
    -f https://storage.googleapis.com/jax-releases/jax_cuda_releases.html && \
    mamba run -p /env \
    python -m pip cache purge

ENV PATH "/env/bin:$PATH"

RUN conda init --reverse && \
    rm -rf $(conda info --base) && \
    rm -f "${HOME}/.condarc" && \
    rm -rf ${HOME}/.conda && \
    rm -rf /opt/conda

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
