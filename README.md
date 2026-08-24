# Arca

**ETH Library Zurich · Data Archive · Digital Preservation Pipeline**

[Arca](#etymology) is the digital preservation pipeline of [ETH Zurich's Data Archive](https://library.ethz.ch/en/collections-and-archives/archiving/digital-long-term-preservation/eth-data-archive.html). It bridges the gap between source systems and permanent preservation by automating the detection, staging, validation, packaging, and deposit of digital assets across heterogeneous source formats.


## Vision

Arca ensures that digital assets are carried safely from their source systems into permanent preservation. The current focus is automating the complete ingest path, from the moment a producer delivers content to the point it is safely deposited into permanent storage. The service architecture and event model are built to extend into retrieval of preserved objects and access provisioning as the system grows.


## About this repository

This is the Arca umbrella repository and the single entry point for understanding, running, and testing the system as a whole. Each service and library lives in its own repo with independent versioning and CI.


## Components

| Name | Type | Role                  | Description |
|---|---|-----------------------|---|
| [`arca`](https://github.com/eth-library/arca) | Infrastructure | Project Umbrella      | Provides shared infrastructure for the full system, including Helm charts, local development environment, and e2e test orchestration |
| [`arca-ops`](https://github.com/eth-library/arca-ops) | Infrastructure | GitOps Configuration  | Manages Kubernetes deployment across environments using ArgoCD applications, environment-specific Helm values, and External Secrets |
| [`arca-models`](https://github.com/eth-library/arca-models) | Library | Domain Models         | Defines shared data model schemas and generates Python and Java bindings for all services |
| [`arca-flow`](https://github.com/eth-library/arca-flow) | Service | Orchestrator Engine   | Manages the pipeline lifecycle by detecting deliveries and coordinating staging, validation, packaging, and deposit |
| `arca-form` | Service | Asset Transformer     | Transforms source system metadata and digital assets into validated submission packages |
| `arca-port` | Service | Storage Gateway      | Provides a unified API over S3, NFS, and SFTP for file transfer, chunked upload, and fixity calculation |
| `arca-track` | Service | Preservation Tracker  | Records every preservation event, enforces the SIP state machine, and provides an immutable audit trail |


## Etymology

Arca takes its name from Latin *arca*, the chest or coffer in which Romans kept what they could not afford to lose.[[1]](#ref-1)[[2]](#ref-2) It belongs to a family of words about keeping things safe: *arcēre*, to shut up or enclose, and *arx*, the citadel, all from a single Proto-Indo-European root meaning "to lock, guard, protect."[[3]](#ref-3)

The Roman historian Livy describes one such chest, dug up at the foot of a hill in Rome: its lid was fastened down with lead, and an inscription on the outside declared what was inside. It held books, said to be those of one of Rome's earliest kings, wrapped in waxed cord and still pristine.[[4]](#ref-4)

This pipeline embodies the same lineage: it receives digital assets from source systems, encloses them in validated preservation packages, and carries them safely into permanent storage. Like an *arca*, it is not the final resting place but the trusted carrier.


## References

<a name="ref-1"></a>[1] Lewis, C.T. & Short, C. (1879). *A Latin Dictionary*. Oxford: Clarendon Press. Entry *arca* — "a place for keeping any thing, a chest, box"; the entry opens "arca, ae, f. arceo". Available via [Perseus Digital Library, Tufts University](https://www.perseus.tufts.edu/hopper/text?doc=Perseus:text:1999.04.0059:entry=arca).

<a name="ref-2"></a>[2] Smith, W., Wayte, W. & Marindin, G.E. (Eds.) (1890). *A Dictionary of Greek and Roman Antiquities*. London: John Murray. Entry *arca* — "a chest or coffer in which the Romans were accustomed to place valuables." Available via [Perseus Digital Library, Tufts University](https://www.perseus.tufts.edu/hopper/text?doc=Perseus:text:1999.04.0063:entry=arca-cn).

<a name="ref-3"></a>[3] Pokorny, J. (1959). *Indogermanisches etymologisches Wörterbuch*, pp. 65–66, s.v. *areq-*, "to lock, guard, protect", with the Latin reflexes *arca*, *arceō* ("to keep, shut up, enclose, defend") and *arx* ("citadel, fortress"). Indexed and glossed in the [Indo-European Lexicon](https://lrc.la.utexas.edu/lex/master/0114), Linguistics Research Center, University of Texas at Austin.

<a name="ref-4"></a>[4] Livy [Titus Livius]. *Ab Urbe Condita* ("From the Founding of the City"), 40.29.3–6: "duae lapideae arcae … inuentae sunt, operculis plumbo deuinctis … duo fasces candelis inuoluti septenos habuere libros, non integros modo sed recentissima specie" ([The Latin Library](https://www.thelatinlibrary.com/livy/liv.40.shtml)). Rendered by Rev. Canon Roberts (1912), New York: E. P. Dutton, as "two stone chests … the lids being fastened down with lead … two bundles tied round with cords steeped in wax, each containing seven books, not only intact but to all appearance new" ([Perseus Digital Library, Tufts University](https://www.perseus.tufts.edu/hopper/text?doc=Perseus%3Aabo%3Aphi%2C0914%2C00140%3A29)).