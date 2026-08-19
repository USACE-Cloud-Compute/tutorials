# Cloud Compute Glossary

This glossary provides definitions for the most important terms you'll encounter when working with Cloud Compute, organized by conceptual grouping for easier reference.

## Core Concepts

**Action**
A function exposed by a Plugin that can be executed as part of a Job. Multiple actions can run sequentially within a single job.

**Compute**
The highest level of the CC hierarchy, equivalent to one `cccli run` command. A Compute contains one or more Events and is described by the compute.json file.

**Compute Environment**
The infrastructure configuration (object store, container runtime, orchestration) that executes CC workloads. Two types: Local Docker and AWS.

**Compute File (compute.json)**
JSON file that bridges plugin and compute manifests, containing provider configuration, plugin references, event structure, and event generator settings.

**Compute Manifest**
JSON file representing the configuration for one or more jobs, including inputs, outputs, actions, data stores, and resource requirements.

**Container**
A Docker-compatible containerized runtime environment that encapsulates the plugin software and its dependencies.

**DAG (Directed Acyclic Graph)**
A graph structure representing job relationships where edges flow in one direction only and cannot loop back. Each Event is one DAG.

**Data Path**
A location reference within a resource (e.g., a specific dataset within an HDF5 file), as opposed to the resource path itself.

**Data Source**
One or more resources referenced from a single data store, consisting of files or external references used as input/output for jobs. Contains paths, data_paths, and store references.

**Dependency**
A relationship between jobs where one job must successfully complete before another can start. Defined in the compute manifest using file names.

**Event**
A set of connected Jobs organized in a DAG. A single Compute may have many Events based on the event generator used.

**Event Generator**
A mechanism for creating multiple instances of the same event DAG with different identifiers. Types: List (default), Array, Stream.

**Job**
A node on the Event DAG representing a single plugin execution with one or more actions run in series.

## Configuration & Execution

**CC_EVENT_IDENTIFIER**
An environment variable injected into each job containing a string identifier unique to that event (e.g., event number, name, or custom value).

**cccli (Cloud Compute CLI)**
The command-line interface tool for interacting with Cloud Compute, formerly known as "Manifestor." Used to run, register, terminate, and monitor computes.

**Concurrency**
The number of jobs that can run simultaneously in the compute environment. Configurable in the compute file provider section.

**Payload**
A JSON document stored in the CC object store containing attributes, store configurations, and data source references needed by a running job. Created when inputs include payload_attributes.

**Payload Attributes**
Key-value pairs passed to jobs, stored in the payload JSON file and accessible via CC SDK. Can include nested arrays and objects.

**Per-Event Loop**
An inner loop configuration that runs each event multiple times with different environment variables, enabling complex job permutations.

**Plugin**
A containerized application that reads inputs and produces outputs by implementing one or more Actions. Registered with CC via plugin manifest.

**Plugin Manifest**
JSON file defining what will run and what resources are needed. Used to register a plugin with the compute provider (analogous to AWS Batch job definition).

## Infrastructure & Storage

**AWS Batch**
Amazon's managed service for running batch computing workloads, used as the container runtime and orchestration layer in AWS compute environments.

**Bucket**
A top-level container in an object storage environment (e.g., S3, Minio) used to organize stored objects.

**Compute Provider**
The underlying system that executes jobs. Types: `docker` (local) and `awsbatch` (AWS).

**Minio**
An open-source, S3-compatible object storage solution used for local Docker compute environments.

**Object Store**
Standards-based file storage modeled after AWS S3 conventions. Examples: AWS S3, Minio, Azure Blob Storage.

**Profile**
A string prefix used to delineate environment variables for a specific store (e.g., "MYSTORE" maps to "MYSTORE_AWS_REGION").

**Queue**
A compute provider queue where jobs are submitted. For Docker: "docker-local". For AWS: user-defined queue name.

**Store**
A configured connection to a remote data source (object store, file system, database) defined with a name, type, profile, and parameters.

## Substitution & Templating

**ATTR Substitution**
Substitution type that replaces placeholders with payload attribute values. Syntax: `{ATTR::attributeName}`

**ENV Substitution**
Substitution type that replaces placeholders with environment variable values. Syntax: `{ENV::VARIABLE_NAME}`

**Substitution**
A templating mechanism using syntax `{{type}::{reference}}` to dynamically populate configuration values at runtime. Types: ENV, ATTR, VAR.

**VAR Substitution**
Substitution type reserved for plugin-specific templating, handled by the plugin at runtime. Syntax: `{VAR::variableName}`

## Resource Management

**Execution Timeout**
Optional timeout in seconds. If a running plugin exceeds this duration, it will be terminated.

**Privileged Mode**
A boolean flag that grants elevated privileges to a container, giving it nearly all the same access as processes on the host machine. Used for special requirements like FUSE file systems.

**Resource Requirements**
Configuration specifying virtual CPUs (VCPU) and memory (MB) allocated to a job. Can be set in plugin manifest and overridden in compute manifest.

**Retry Attempts**
Integer representing the number of times a plugin will retry if it fails (default: 0).

**VCPU (Virtual CPU)**
The number of virtual CPU threads allocated to a container. In local Docker: threads from local CPU. In AWS EC2: threads from host EC2 system.

## Event Generator Types

**Array Event Generator**
Creates a numeric range of event identifiers. Configured with a start and end value (e.g., events 1-1000).

**List Event Generator**
The default generator that creates a single event with identifier "0". Used when no generator is specified.

**Stream Event Generator**
Reads event identifiers from a delimited file, allowing custom string values or non-sequential numbers to be used as event identifiers.

## See Also

- [CloudCompute for Dummies](./01_cc-for-dummies.md) - Introduction to core concepts
- [Plugin Manifest Reference](./05_plugin-manifest.md) - Detailed plugin configuration
- [Compute Manifest Reference](./06_compute-manifest.md) - Detailed compute configuration
- [Compute File Reference](./07_compute-file.md) - Compute file structure and options
