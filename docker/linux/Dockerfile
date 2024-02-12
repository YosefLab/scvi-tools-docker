ARG PYTHON_VERSION=3.11
ARG CUDA_VERSION=11
FROM scverse/scvi-tools:py${PYTHON_VERSION}-cu${CUDA_VERSION}-base

ARG SCVI_TOOLS_VERSION=latest
ARG BRANCH_NAME=main
ARG DEPENDENCIES=""
ENV SCVI_TOOLS_VERSION=${SCVI_TOOLS_VERSION}
ENV BRANCH_NAME=${BRANCH_NAME}
ENV DEPENDENCIES=${DEPENDENCIES}
RUN if [ "$SCVI_TOOLS_VERSION" = "latest" ]; then \
        pip install --no-cache-dir "scvi-tools[${DEPENDENCIES}] @ git+https://github.com/scverse/scvi-tools@${BRANCH_NAME}" ; \
    elif [ "$SCVI_TOOLS_VERSION" = "stable" ]; then \
        pip install -U --no-cache-dir "scvi-tools[${DEPENDENCIES}]" ; \
    else \
        pip install --no-cache-dir "scvi-tools[${DEPENDENCIES}]==${SCVI_TOOLS_VERSION}" ; \
    fi && \
        pip cache purge
