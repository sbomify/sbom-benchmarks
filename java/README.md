# SBOM Generation for Java

[![Java](https://github.com/sbomify/sbom-benchmarks/actions/workflows/java.yml/badge.svg)](https://github.com/sbomify/sbom-benchmarks/actions/workflows/java.yml)

## Target Project

This benchmark uses [Keycloak](https://github.com/keycloak/keycloak), an Open Source Identity and Access Management solution for modern applications and services. Keycloak is a large-scale Java/Maven project with complex dependency management, making it an excellent benchmark target.

**Version:** 26.4.7

## Tools

Tools from the sbomify [resource list](https://sbomify.com/resources/), specifically:

* Trivy
* Syft
* sbomify github-action

## Process

The benchmark workflow:

1. Clones the Keycloak repository at the specified tag
2. Runs each SBOM generator against the project's `pom.xml` and source tree
3. Scores each generated SBOM using sbomqs
4. Produces a comparison table in the workflow summary

The full process is automated and you can see the exact commands in [java.yml](https://github.com/sbomify/sbom-benchmarks/blob/master/.github/workflows/java.yml).

If you look at the [Java CI/CD run](https://github.com/sbomify/sbom-benchmarks/actions/workflows/java.yml), you can see the quality score of the SBOMs (from `sbomqs`) as well as download the actual SBOMs as artifacts.

## Why Keycloak?

Keycloak was chosen as a benchmark target because:

- **Complex dependency tree**: Hundreds of Maven dependencies across multiple modules
- **Real-world project**: Actively maintained, widely deployed enterprise software
- **Mixed ecosystem**: Combines Java libraries, JavaScript frontend components, and more
- **Multi-module Maven**: Tests SBOM generators' ability to handle complex build structures
