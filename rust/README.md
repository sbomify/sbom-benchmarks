# SBOM Generation for Rust

[![Rust](https://github.com/sbomify/sbom-benchmarks/actions/workflows/rust.yml/badge.svg)](https://github.com/sbomify/sbom-benchmarks/actions/workflows/rust.yml)

## Target Project

This benchmark uses [quiche](https://github.com/cloudflare/quiche), Cloudflare's implementation of the QUIC transport protocol and HTTP/3. It's a production-grade Rust project used in Cloudflare's infrastructure.

**Version:** 0.24.5

## Tools

Tools from the sbomify [resource list](https://sbomify.com/resources/), specifically:

* Trivy
* Syft
* sbomify github-action

## Process

The benchmark workflow:

1. Clones the quiche repository at the specified tag
2. Runs each SBOM generator against the project's `Cargo.lock` and source tree
3. Scores each generated SBOM using sbomqs
4. Produces a comparison table in the workflow summary

The full process is automated and you can see the exact commands in [rust.yml](https://github.com/sbomify/sbom-benchmarks/blob/master/.github/workflows/rust.yml).

If you look at the [Rust CI/CD run](https://github.com/sbomify/sbom-benchmarks/actions/workflows/rust.yml), you can see the quality score of the SBOMs (from `sbomqs`) as well as download the actual SBOMs as artifacts.

## Why quiche?

quiche was chosen as a benchmark target because:

- **Production Rust**: Used in Cloudflare's production infrastructure serving millions of requests
- **Complex dependencies**: Multiple crates with native dependencies (BoringSSL)
- **Workspace structure**: Multi-crate Cargo workspace tests SBOM generators' Rust support
- **Well-maintained**: Active development with regular releases
- **Popular**: 11k+ GitHub stars, widely used in the Rust ecosystem
