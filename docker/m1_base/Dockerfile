FROM ubuntu:latest as ubuntu

RUN curl -fsSLo Miniforge3.sh "https://github.com/conda-forge/miniforge/releases/latest/download/Miniforge3-MacOSX-$(uname -m).sh" && \
    bash Miniforge3.sh -b -p "${HOME}/conda" && \
    source "${HOME}/conda/etc/profile.d/conda.sh" && \
    source "${HOME}/conda/etc/profile.d/mamba.sh" && \
    conda activate && \
    rm Miniforge3.sh