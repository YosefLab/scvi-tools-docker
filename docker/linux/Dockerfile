ARG PYTHON_VERSION=3.11
ARG CUDA_VERSION=11
FROM scverse/scvi-tools:py${PYTHON_VERSION}-cu${CUDA_VERSION}-base AS base

FROM base AS latest
ARG DEPENDENCIES=""
ENV DEPENDENCIES=${DEPENDENCIES}
RUN pip install --no-cache-dir "scvi-tools[${DEPENDENCIES}] @ git+https://github.com/scverse/scvi-tools" && \
    pip cache purge

FROM base AS stable
ARG DEPENDENCIES=""
ENV DEPENDENCIES=${DEPENDENCIES}
RUN pip install -U --no-cache-dir "scvi-tools[${DEPENDENCIES}]" && \
    pip cache purge

FROM base AS branch
ARG SCVI_TOOLS_VERSION=main
ARG DEPENDENCIES=""
ENV SCVI_TOOLS_VERSION=${SCVI_TOOLS_VERSION}
ENV DEPENDENCIES=${DEPENDENCIES}
RUN pip install --no-cache-dir "scvi-tools[${DEPENDENCIES}] @ git+https://github.com/scverse/scvi-tools@${SCVI_TOOLS_VERSION}" && \
    pip cache purge

FROM base AS semver
ARG SCVI_TOOLS_VERSION=latest
ARG DEPENDENCIES=""
ENV SCVI_TOOLS_VERSION=${SCVI_TOOLS_VERSION}
ENV DEPENDENCIES=${DEPENDENCIES}
RUN pip install --no-cache-dir "scvi-tools[${DEPENDENCIES}]==${SCVI_TOOLS_VERSION}" && \
    pip cache purge
