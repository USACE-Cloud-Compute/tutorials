# Cloud Compute

Welcome to Cloud Compute (CC) - a USACE-developed orchestration framework for running containerized computational workloads at scale, either locally or in cloud environments.

## What is Cloud Compute?

Cloud Compute is a set of tools and conventions that allow you to organize and orchestrate compute jobs in the cloud or on your local desktop. Built by USACE and optimized for hydrologic/hydraulic (H&H) models in massively parallel model runs, CC is flexible enough to accommodate many different workflows.

## Quick Start

New to Cloud Compute? Follow these steps to get started:

1. **[Read the Introduction](./docs/01_cc-for-dummies.md)** - Learn the core concepts and terminology
2. **Set up your environment** - Choose one:
   - [Local Docker Setup](./docs/02a_setting-up-local-docker.md) - Test plugins and configurations on your machine
   - [AWS Setup](./docs/02b_setting-up-aws.md) - Run compute at scale in the cloud
3. **[Install the CC CLI](./docs/03_cc-cli.md)** - Download and configure the command-line tool
4. **[Run the Hello World Tutorial](./tutorials/hello-world/README.md)** - Get hands-on experience with your first compute

## Documentation

- [Complete Documentation Index](./docs/README.md) - Full list of documentation topics
- [Advanced Topics](./docs/04_advanced-topics.md) - Plugin registration, manifest authoring, and more
- [Glossary](./docs/08_glossary.md) - Comprehensive reference of CC terminology

## Prerequisites

Before diving into Cloud Compute, you should have:

- General Docker knowledge (experience running containers, bonus if you've built custom images)
- Command-line comfort (CC is primarily a CLI tool)

## Tutorials

### General Tutorials
- [Hello World](./tutorials/hello-world/README.md) - Basic introduction to running computes

### FFRD Program Tutorials
> **Note:** Tutorial documentation in the `/tutorials/FFRD` folder assumes familiarity with the Future of Flood Risk Data (FFRD) program and Standard Operating Procedures (SOP). These tutorials are intended for Federal Employees and contractors working on the FFRD program and are not designed for general audiences. Before using the FFRD tutorials, familiarize yourself with the FFRD SOP and associated job aids.

## Support

- [GitHub Discussions](https://github.com/orgs/USACE-Cloud-Compute/discussions) - Ask questions and share knowledge
- [CC CLI Releases](https://github.com/USACE-Cloud-Compute/cloudcompute-cli/releases) - Download the latest CLI version
