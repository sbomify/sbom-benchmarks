# SBOM Generation for Go

[![Go](https://github.com/sbomify/sbom-benchmarks/actions/workflows/go.yml/badge.svg)](https://github.com/sbomify/sbom-benchmarks/actions/workflows/go.yml)

## Target Project

This benchmark uses [OSV Scanner](https://github.com/google/osv-scanner), Google's vulnerability scanner that uses the OSV database to find known vulnerabilities in project dependencies. It's a production-grade Go project with a well-structured dependency tree.

**Version:** 2.3.1

## Tools

Tools from the sbomify [resource list](https://sbomify.com/resources/), specifically:

* Trivy
* Syft
* sbomify github-action

## Process

The benchmark workflow:

1. Clones the OSV Scanner repository at the specified tag
2. Runs each SBOM generator against the project's `go.mod` and source tree
3. Scores each generated SBOM using sbomqs
4. Produces a comparison table in the workflow summary

The full process is automated and you can see the exact commands in [go.yml](https://github.com/sbomify/sbom-benchmarks/blob/master/.github/workflows/go.yml).

If you look at the [Go CI/CD run](https://github.com/sbomify/sbom-benchmarks/actions/workflows/go.yml), you can see the quality score of the SBOMs (from `sbomqs`) as well as download the actual SBOMs as artifacts.

## Why OSV Scanner?

OSV Scanner was chosen as a benchmark target because:

- **Go modules**: Clean Go module dependency management via `go.mod`
- **Security tooling**: Ironically, it's a security tool itself - interesting to SBOM a vulnerability scanner
- **Google-maintained**: High-quality codebase with good dependency hygiene
- **Moderate complexity**: Not too simple, not too complex - good middle-ground benchmark
