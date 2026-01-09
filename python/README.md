# SBOM Generation for Python

[![Python](https://github.com/sbomify/sbom-benchmarks/actions/workflows/python.yml/badge.svg)](https://github.com/sbomify/sbom-benchmarks/actions/workflows/python.yml)

## Target

The `requirements.txt` is **intentionally minimal** - it only lists direct dependencies (Django and its immediate deps). This tests each SBOM tool's ability to resolve **transitive dependencies**.

A quality SBOM generator should discover all indirect dependencies, not just what's explicitly listed in the lockfile.

## Tools

Tools from the sbomify [resource list](https://sbomify.com/resources/#Python):

* Trivy
* Syft
* sbomify github-action
* sbom4python
* cyclonedx-python

The full process is automated and you can see the exact commands we run in [python.yml](https://github.com/sbomify/sbom-benchmarks/blob/master/.github/workflows/python.yml).

If you look at the [Python CI/CD run](https://github.com/sbomify/sbom-benchmarks/actions/workflows/python.yml), you can see the quality score of the SBOMs (from `sbomqs`) as well as download the actual SBOMs as artifacts.
