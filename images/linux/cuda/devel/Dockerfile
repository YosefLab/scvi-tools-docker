ARG PYTHON_VERSION=3.11
ARG CUDA_VERSION=11
FROM martinkim0/scvi-tools:py${PYTHON_VERSION}-cu${CUDA_VERSION}-base

ARG SCVI_TOOLS_VERSION=latest
ENV SCVI_TOOLS_VERSION=${SCVI_TOOLS_VERSION}
RUN if [ "$SCVI_TOOLS_VERSION" = "latest" ]; then \
        pip install --no-cache-dir "scvi-tools[all] @ git+https://github.com/scverse/scvi-tools" \
    elif [ "$SCVI_TOOLS_VERSION" = "stable" ]; then \
        pip install --no-cache-dir "scvi-tools[all]" \
    else \
        pip install --no-cache-dir "scvi-tools[all]==${SCVI_TOOLS_VERSION}" \
    fi && \
        pip cache purge
