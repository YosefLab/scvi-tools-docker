ARG PYTHON_VERSION=3.11
ARG CUDA_VERSION=11
FROM scverse/scvi-tools:py${PYTHON_VERSION}-cu${CUDA_VERSION}-base

ARG SCVI_TOOLS_VERSION=latest
ARG DEPENDENCIES=""
ENV SCVI_TOOLS_VERSION=${SCVI_TOOLS_VERSION}
ENV DEPENDENCIES=${DEPENDENCIES}
RUN if [ "${SCVI_TOOLS_VERSION}" = "latest" ]; then \
        pip install --no-cache-dir "scvi-tools[${DEPENDENCIES}] @ git+https://github.com/scverse/scvi-tools" ; \
    elif [ "${SCVI_TOOLS_VERSION}" = "stable" ]; then \
        pip install -U --no-cache-dir "scvi-tools[${DEPENDENCIES}]" ; \
    elif [ "${SCVI_TOOLS_VERSION}" =~ ^\d+\.\d+\.x$ ]; then \
        pip install --no-cache-dir "scvi-tools[${DEPENDENCIES}] @ git+https://github.com/scverse/scvi-tools@${SCVI_TOOLS_VERSION}" ; \
    else \
        pip install --no-cache-dir "scvi-tools[${DEPENDENCIES}]==${SCVI_TOOLS_VERSION}" ; \
    fi && \
        pip cache purge
