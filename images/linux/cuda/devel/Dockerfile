ARG PYTHON_VERSION=3.11
ARG CUDA_VERSION=11
FROM martinkim0/scvi-tools:py${PYTHON_VERSION}-cu${CUDA_VERSION}-base

ARG SCVI_TOOLS_VERSION=latest
ENV SCVI_TOOLS_VERSION=${SCVI_TOOLS_VERSION}
RUN if [ "$SCVI_TOOLS_VERSION" = "latest" ]; then \
        pip install "scvi-tools[all] @ git+https://github.com/scverse/scvi-tools" && \
        pip cache purge ; \
    elif [ "$SCVI_TOOLS_VERSION" = "stable" ]; then \
        pip install "scvi-tools[all]" && \
        pip cache purge ; \
    else \
        pip install "scvi-tools[all]==${SCVI_TOOLS_VERSION}" && \
        pip cache purge ; \
    fi && \
        pip cache purge
