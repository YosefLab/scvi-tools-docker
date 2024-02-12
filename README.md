<img src="https://github.com/scverse/scvi-tools/blob/main/docs/_static/scvi-tools-horizontal.svg?raw=true" width="400" alt="scvi-tools">

[![Discourse](https://img.shields.io/discourse/posts?color=yellow&logo=discourse&server=https%3A%2F%2Fdiscourse.scverse.org)](https://discourse.scverse.org/)
[![Chat](https://img.shields.io/badge/zulip-join_chat-brightgreen.svg)](https://scverse.zulipchat.com/)
[![Powered by NumFOCUS][badge-numfocus]][link-numfocus]

[scvi-tools](https://scvi-tools.org/) (single-cell variational inference
tools) is a package for probabilistic modeling and analysis of single-cell omics
data, built on top of [PyTorch](https://pytorch.org) and
[AnnData](https://anndata.readthedocs.io/en/latest/).

[//]: # "numfocus-fiscal-sponsor-attribution"

scvi-tools is part of the scverse project ([website](https://scverse.org), [governance](https://scverse.org/about/roles)) and is fiscally sponsored by [NumFOCUS](https://numfocus.org/).
Please consider making a tax-deductible [donation](https://numfocus.org/donate-to-scverse) to help the project pay for developer time, professional services, travel, workshops, and a variety of other needs.

<a href="https://numfocus.org/project/scverse">
  <img
    src="https://raw.githubusercontent.com/numfocus/templates/master/images/numfocus-logo.png"
    width="200"
  >
</a>

[badge-numfocus]: https://img.shields.io/badge/powered%20by-NumFOCUS-orange.svg?style=flat&colorA=E1523D&colorB=007D8A
[link-numfocus]: http://numfocus.org

# Docker images

This repository contains the source Dockerfiles for the scvi-tools [Docker images](https://hub.docker.com/repository/docker/scverse/scvi-tools/general).

## Tags

`py{PYTHON_VERSION}-cu{CUDA_VERSION}-base`: CUDA-enabled PyTorch and JAX installations - updated weekly Sunday at 05:00 PST

-   Updated weekly Sunday at 05:00 PST
-   We currently build images for `PYTHON_VERSION=[3.9, 3.10, 3.11]` and `CUDA_VERSION=[11]`

`py{PYTHON_VERSION}-cu{CUDA_VERSION}-runtime-{latest/stable/sem_ver}`: `base` image with only runtime dependencies

-   `latest`: Updated daily at 12:00 PST
-   `stable`: Alias for the newest `sem_ver`
-   `sem_ver`: Ppdated with each new stable release on the [main repository](https://github.com/scverse/scvi-tools)

`py{PYTHON_VERSION}-cu{CUDA_VERSION}-devel-{latest/stable/sem_ver}`: `base` image with development dependencies

-   `latest`: Updated daily at 12:00 PST
-   `stable`: Alias for the newest `sem_ver`
-   `sem_ver`: Updated with each new stable release on the [main repository](https://github.com/scverse/scvi-tools)

`py{PYTHON_VERSION}-cu{CUDA_VERSION}-devel-{latest/stable/sem_ver}`: `base` image with tutorial dependencies

-   `latest`: Updated daily at 12:00 PST
-   `stable`: Alias for the newest `sem_ver`
-   `sem_ver`: Updated with each new stable release on the [main repository](https://github.com/scverse/scvi-tools)

# Reference

If you use `scvi-tools` in your work, please cite

> **A Python library for probabilistic analysis of single-cell omics data**
>
> Adam Gayoso, Romain Lopez, Galen Xing, Pierre Boyeau, Valeh Valiollah Pour Amiri, Justin Hong, Katherine Wu, Michael Jayasuriya, Edouard Mehlman, Maxime Langevin, Yining Liu, Jules Samaran, Gabriel Misrachi, Achille Nazaret, Oscar Clivio, Chenling Xu, Tal Ashuach, Mariano Gabitto, Mohammad Lotfollahi, Valentine Svensson, Eduardo da Veiga Beltrame, Vitalii Kleshchevnikov, Carlos Talavera-López, Lior Pachter, Fabian J. Theis, Aaron Streets, Michael I. Jordan, Jeffrey Regier & Nir Yosef
>
> _Nature Biotechnology_ 2022 Feb 07. doi: [10.1038/s41587-021-01206-w](https://doi.org/10.1038/s41587-021-01206-w).

along with the publicaton describing the model used.

You can cite the scverse publication as follows:

> **The scverse project provides a computational ecosystem for single-cell omics data analysis**
>
> Isaac Virshup, Danila Bredikhin, Lukas Heumos, Giovanni Palla, Gregor Sturm, Adam Gayoso, Ilia Kats, Mikaela Koutrouli, Scverse Community, Bonnie Berger, Dana Pe’er, Aviv Regev, Sarah A. Teichmann, Francesca Finotello, F. Alexander Wolf, Nir Yosef, Oliver Stegle & Fabian J. Theis
>
> _Nature Biotechnology_ 2023 Apr 10. doi: [10.1038/s41587-023-01733-8](https://doi.org/10.1038/s41587-023-01733-8).
