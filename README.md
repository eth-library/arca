# Arca

**ETH Library Zurich · Data Archive · Digital Preservation Pipeline**

[Arca](#etymology) is the digital preservation pipeline of [ETH Zurich's Data Archive](https://library.ethz.ch/en/collections-and-archives/archiving/digital-long-term-preservation/eth-data-archive.html). It bridges the gap between producer systems and permanent preservation by automating the detection, staging, validation, packaging, and deposit of digital assets across heterogeneous source formats.


## Vision

Arca ensures that digital assets are carried safely from their source systems into permanent preservation. The current focus is automating the complete ingest path, from the moment a producer delivers content to the point it is safely deposited into permanent storage. The service architecture and event model are built to extend into retrieval of preserved objects and access provisioning as the system grows.


## About this repository

This is the Arca umbrella repository and the single entry point for understanding, running, and testing the system as a whole. Each service and library lives in its own repo with independent versioning and CI.


## Components

| Name | Type | Role | Description |
|---|---|---|---|
| [`arca`](https://github.com/eth-library/arca) | Infrastructure | Project Umbrella | Provides shared infrastructure for the full system, including Helm charts, local development environment, and e2e test orchestration |
| [`arca-ops`](https://github.com/eth-library/arca-ops) | Infrastructure | GitOps Configuration | Manages Kubernetes deployment across environments using ArgoCD applications, environment-specific Helm values, and External Secrets |
| [`arca-models`](https://github.com/eth-library/arca-models) | Library | Domain Models | Defines shared data model schemas and generates Python and Java bindings for all services |
| `arca-desk` | Service | Operator UI | Provides a web interface for monitoring pipeline activity and triggering manual actions |
| [`arca-flow`](https://github.com/eth-library/arca-flow) | Service | Pipeline Orchestrator | Manages the pipeline lifecycle by detecting deliveries and coordinating staging, validation, packaging, and deposit |
| `arca-form` | Service | Asset Transformer | Transforms producer metadata and digital assets into validated submission packages |
| `arca-hub` | Service | Configuration Central | Serves producer and location configuration, validates against schemas, and tracks service versions |
| `arca-port` | Service | Storage Gateway | Provides a unified API over S3, NFS, and SFTP for file transfer, chunked upload, and fixity calculation |
| `arca-track` | Service | Preservation Tracker | Records every preservation event, enforces the SIP state machine, and provides an immutable audit trail |
| `arca-samples` | Data | Test Fixtures | Provides lightweight per-producer sample deliveries for local development and e2e testing |


## Etymology

Arca takes its name from Latin *arca*, a vessel for safeguarding valuables.[[1]](#references)[[2]](#references) The word traces to *arcēre* (to enclose, guard) and ultimately Proto-Indo-European *h₂erk-* (to hold, contain, guard).[[3]](#references) The system embodies this lineage: it receives digital assets from producers, encloses them in validated preservation packages, and carries them safely into permanent storage. Like an *arca*, it is not the final resting place but the trusted carrier.


## References

[1] Lewis, C.T. & Short, C. (1879). *A Latin Dictionary*. Oxford: Clarendon Press. Entry: *arca, arcae, f.* — "box, chest; strong-box, coffer; a place of safe-keeping." Available via [Perseus Digital Library, Tufts University](https://www.perseus.tufts.edu/hopper/text?doc=Perseus:text:1999.04.0059:entry=arca).

[2] Smith, W. (1890). *A Dictionary of Greek and Roman Antiquities*. London: John Murray. Entry: *arca* — "a chest or coffer in which the Romans were accustomed to place valuables." Available via [Perseus Digital Library, Tufts University](http://www.perseus.tufts.edu/hopper/text?doc=Perseus:text:1999.04.0063:entry=arca-cn).

[3] Harper, D. "arcane." *Online Etymology Dictionary*. Available at [etymonline.com/word/arcane](https://www.etymonline.com/word/arcane).