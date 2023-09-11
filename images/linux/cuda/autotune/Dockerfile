FROM martinkim0/scvi-tools:py3.11-cu11-base

RUN pip install "scvi-tools[autotune,census] @ git+https://github.com/scverse/scvi-tools@main" && \
    pip cache purge
