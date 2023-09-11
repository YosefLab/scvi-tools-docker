FROM martinkim0/scvi-tools:py${PYTHON_VERSION}-cu${CUDA_VERSION}-base

RUN pip install "scvi-tools[autotune,census] @ git+https://github.com/scverse/scvi-tools@main" && \
    pip cache purge
