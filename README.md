# SBOM Benchmarking

[![Python](https://github.com/sbomify/sbom-benchmarks/actions/workflows/python.yml/badge.svg)](https://github.com/sbomify/sbom-benchmarks/actions/workflows/python.yml)
[![JavaScript](https://github.com/sbomify/sbom-benchmarks/actions/workflows/javascript.yml/badge.svg)](https://github.com/sbomify/sbom-benchmarks/actions/workflows/javascript.yml)
[![Java](https://github.com/sbomify/sbom-benchmarks/actions/workflows/java.yml/badge.svg)](https://github.com/sbomify/sbom-benchmarks/actions/workflows/java.yml)
[![Go](https://github.com/sbomify/sbom-benchmarks/actions/workflows/go.yml/badge.svg)](https://github.com/sbomify/sbom-benchmarks/actions/workflows/go.yml)
[![Rust](https://github.com/sbomify/sbom-benchmarks/actions/workflows/rust.yml/badge.svg)](https://github.com/sbomify/sbom-benchmarks/actions/workflows/rust.yml)
[![Docker](https://github.com/sbomify/sbom-benchmarks/actions/workflows/docker.yml/badge.svg)](https://github.com/sbomify/sbom-benchmarks/actions/workflows/docker.yml)

This repository is designed to generate Software Bill of Materials (SBOMs) using a comprehensive benchmark across a wide variety of tools on defined targets across multiple programming languages. The goal is to provide a consistent and standardized method for evaluating and comparing the effectiveness and accuracy of various SBOM generation tools, helping users to identify the best tool for their specific needs.

The list of tools used is pulled from our [SBOM resources](https://sbomify.com/resources/) page that includes a comprehensive list of SBOM tools.

## Features

* **Multi-Tool Support**: Run benchmarks across a diverse set of SBOM generation tools including Trivy, Syft, and sbomify.
* **Cross-Language Compatibility**: Supports multiple programming languages (Python, JavaScript, Java, Go, Rust) and container images.
* **Automated Workflow**: Easily set up and execute benchmarks with minimal manual intervention.
* **Detailed Reports**: Generate detailed comparisons and summaries of the SBOMs produced by different tools, highlighting strengths and weaknesses.
* **Quality Scoring**: Each SBOM is scored using [sbomqs](https://github.com/interlynk-io/sbomqs) to measure SBOM quality.
* **Extensibility**: Add support for new tools or languages with minimal configuration changes.

## Benchmarked Tools

| Tool | Description |
|------|-------------|
| [Trivy](https://github.com/aquasecurity/trivy) | Comprehensive security scanner with SBOM generation |
| [Syft](https://github.com/anchore/syft) | CLI tool and library for generating SBOMs |
| [sbomify](https://github.com/sbomify/github-action) | SBOM generation with enrichment from package registries |
| [cyclonedx-python](https://github.com/CycloneDX/cyclonedx-python) | Native Python SBOM generator (Python benchmarks only) |
| [sbom4python](https://github.com/anthonyharrison/sbom4python) | Python-specific SBOM generator (Python benchmarks only) |

## Benchmark Targets

| Target | Language/Type | Project | Description |
|--------|--------------|---------|-------------|
| [Python](python/) | Python | Django | Python web framework dependencies |
| [JavaScript](javascript/) | JavaScript/TypeScript | workers-sdk | Cloudflare's Wrangler CLI monorepo |
| [Java](java/) | Java/Maven | Keycloak | Enterprise IAM with complex Maven dependencies |
| [Go](go/) | Go | OSV Scanner | Go modules-based security tool |
| [Rust](rust/) | Rust | quiche | Cloudflare's QUIC/HTTP3 implementation |
| [Docker](docker/) | Container | nginx + vim | Container image with added packages |

## Run Details

Each benchmark runs automatically on push to master and produces:
- SBOMs in both CycloneDX and SPDX formats (where supported)
- Quality scores from sbomqs
- Comparison tables in the GitHub Actions summary

Click on any badge above to see the latest benchmark results.

### Detailed Documentation

* [Python Benchmark](https://github.com/sbomify/sbom-benchmarks/tree/master/python) - Django requirements.txt
* [JavaScript Benchmark](https://github.com/sbomify/sbom-benchmarks/tree/master/javascript) - Cloudflare workers-sdk (pnpm-lock.yaml)
* [Java Benchmark](https://github.com/sbomify/sbom-benchmarks/tree/master/java) - Keycloak (Maven/pom.xml)
* [Go Benchmark](https://github.com/sbomify/sbom-benchmarks/tree/master/go) - OSV Scanner (go.mod)
* [Rust Benchmark](https://github.com/sbomify/sbom-benchmarks/tree/master/rust) - Cloudflare quiche (Cargo.lock)
* [Docker Benchmark](https://github.com/sbomify/sbom-benchmarks/tree/master/docker) - nginx container with vim installed

## Tool Versions

Current tool versions used in benchmarks:

| Tool | Version |
|------|---------|
| Trivy | 0.68.2 |
| Syft | 1.39.0 |
| sbomqs | 2.0.2 |
| cyclonedx-bom | 7.2.1 |
| sbom4python | 0.12.4 |
