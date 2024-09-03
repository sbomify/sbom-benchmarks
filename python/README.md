# SBOM Generation for Python
[![Python](https://github.com/sbomify/sbom-benchmarks/actions/workflows/python.yml/badge.svg)](https://github.com/sbomify/sbom-benchmarks/actions/workflows/python.yml)

## Setup

Generate `requirements.txt`:

```bash
$ pip install Django
$ pip freeze > requirements.txt
```

## Tools

Tools from the sbomify [resource list](https://sbomify.com/resources/#Python), but in short they are:

* Trivy
* Syft
* sbom4python
* cyclonedx-python

The full process is automated and you can see the exact commands we run in [python.yml](https://github.com/sbomify/sbom-benchmarks/blob/master/.github/workflows/python.yml).

If you look at the [Python CI/CD run](https://github.com/sbomify/sbom-benchmarks/actions/workflows/python.yml), you can also see the quality score of the SBOMs (from `sbomqsq`) as well as downloading the actual SBOMs as artifact.
