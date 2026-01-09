# SBOM Generation for JavaScript

[![JavaScript](https://github.com/sbomify/sbom-benchmarks/actions/workflows/javascript.yml/badge.svg)](https://github.com/sbomify/sbom-benchmarks/actions/workflows/javascript.yml)

## Target Project

This benchmark uses [workers-sdk](https://github.com/cloudflare/workers-sdk), Cloudflare's monorepo containing Wrangler (the CLI for Cloudflare Workers), Miniflare, and related tooling. It's a large-scale TypeScript/JavaScript project with complex dependency management.

**Version:** wrangler@3.99.0

## Tools

Tools from the sbomify [resource list](https://sbomify.com/resources/), specifically:

* Trivy
* Syft
* sbomify github-action

## Process

The benchmark workflow:

1. Clones the workers-sdk repository at the specified tag
2. Runs each SBOM generator against the project's `pnpm-lock.yaml` and source tree
3. Scores each generated SBOM using sbomqs
4. Produces a comparison table in the workflow summary

The full process is automated and you can see the exact commands in [javascript.yml](https://github.com/sbomify/sbom-benchmarks/blob/master/.github/workflows/javascript.yml).

If you look at the [JavaScript CI/CD run](https://github.com/sbomify/sbom-benchmarks/actions/workflows/javascript.yml), you can see the quality score of the SBOMs (from `sbomqs`) as well as download the actual SBOMs as artifacts.

## Why workers-sdk?

workers-sdk was chosen as a benchmark target because:

- **Monorepo structure**: Multiple packages (Wrangler, Miniflare, C3) in a pnpm workspace
- **Production TypeScript**: Powers Cloudflare's developer tooling used by millions
- **Complex dependencies**: Hundreds of npm packages across multiple workspaces
- **pnpm lockfile**: Tests SBOM generators' support for modern package managers
- **Widely used**: 106k+ dependent repositories on GitHub
