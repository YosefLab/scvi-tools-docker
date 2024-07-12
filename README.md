<a href="https://scvi-tools.org/">
  <img
    src="https://github.com/scverse/scvi-tools/blob/main/docs/_static/scvi-tools-horizontal.svg?raw=true"
    width="400"
    alt="scvi-tools"
  >
</a>

[![linux (cuda, base)][linux-cuda-base-badge]][linux-cuda-base-link]
[![linux (cuda, latest)][linux-cuda-latest-badge]][linux-cuda-latest-link]

[scvi-tools] (single-cell variational inference tools) is a package for probabilistic modeling and
analysis of single-cell omics data, built on top of [PyTorch] and [AnnData].

# Docker images

IMPORTANT: This repository is deprecated. Please see the updated images in the [GitHub Container
Registry](https://github.com/scverse/scvi-tools/pkgs/container/scvi-tools)

This repository contains the source files for our [Docker images].

## Tags

`py{PYTHON_VERSION}-cu{CUDA_VERSION}-base`: CUDA-based PyTorch and JAX installations

- Updated weekly Sunday at 05:00 PST
- We currently build images for `PYTHON_VERSION=[3.9, 3.10, 3.11]` and `CUDA_VERSION=[11, 12]`

`py{PYTHON_VERSION}-cu{CUDA_VERSION}-runtime-{latest/stable/semver}`: `base` image with runtime
dependencies

- `latest`: Updated daily at 12:00 PST
- `stable`: Alias for the most recent `semver`
- `semver`: Updated with each new stable release on the [main repository]

`py{PYTHON_VERSION}-cu{CUDA_VERSION}-dev-{latest/stable/semver}`: `base` image with development
dependencies

- `latest`: Updated daily at 12:00 PST
- `stable`: Alias for the most recent `semver`
- `semver`: Updated with each new stable release on the [main repository]

`py{PYTHON_VERSION}-cu{CUDA_VERSION}-tutorials-{latest/stable/semver}`: `base` image with tutorial
dependencies

- `latest`: Updated daily at 12:00 PST
- `stable`: Alias for the most recent `semver`
- `semver`: Updated with each new stable release on the [main repository]

[anndata]: https://anndata.readthedocs.io/en/latest/
[docker images]: https://hub.docker.com/repository/docker/scverse/scvi-tools/general
[linux-cuda-base-badge]: https://github.com/YosefLab/scvi-tools-docker/actions/workflows/linux_cuda_base.yaml/badge.svg
[linux-cuda-base-link]: https://github.com/YosefLab/scvi-tools-docker/actions/workflows/linux_cuda_base.yaml
[linux-cuda-latest-badge]: https://github.com/YosefLab/scvi-tools-docker/actions/workflows/linux_cuda_latest_scheduled.yaml/badge.svg
[linux-cuda-latest-link]: https://github.com/YosefLab/scvi-tools-docker/actions/workflows/linux_cuda_latest_scheduled.yaml
[main repository]: https://github.com/scverse/scvi-tools
[pytorch]: https://pytorch.org
[scvi-tools]: https://scvi-tools.org/
