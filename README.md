CenCaM-Net Anonymous Reproducibility Repository
This repository contains the anonymous reproducibility package for CenCaM-Net. The package provides the source code, configuration files, data contracts, preprocessing utilities, training and evaluation scripts, calibration components, experiment records, documentation, integrity manifests, and automated tests used to organize the CenCaM-Net workflow.
The repository does not redistribute raw datasets, private resources, credentials, local machine paths, or trained checkpoints.
Repository Contents
.
├── configs/       Experiment and controlled-study configurations
├── data/          Public-data registration instructions and source metadata
├── docs/          Reproducibility, compute, schema, and execution documentation
├── manifests/     Dataset, split, repository, and file-integrity manifests
├── records/       Structured manuscript-aligned record files
├── scripts/       Data, training, calibration, evaluation, and audit utilities
├── src/cencam/    CenCaM-Net implementation
└── tests/         Automated unit and protocol tests
Source Package
The src/cencam/ directory contains the Python implementation of the repository components.
Data Components
The src/cencam/data/ package contains:
- canonical event-schema definitions;
- dataset wrappers for fixed-shape training and evaluation inputs;
- chronological user- and item-history construction;
- strictly past-event history controls;
- purchase and refund label-maturity derivation;
- right-censoring and event-bin construction;
- chronological shard preparation; and
- stable identifier and split-handling utilities.
Model Components
The src/cencam/model/ package contains:
- the main CenCaMNet model definition;
- shared dense and categorical field tokenization;
- relative-time embeddings;
- separate user- and item-history encoders;
- grouped complex sequence encoding;
- current-click-guided history pooling;
- asymmetric shared-private expert routing;
- conversion-to-refund feature transfer;
- cascaded discrete-hazard output heads;
- mature-label binary output adapters; and
- matched baseline model definitions.
Learning and Evaluation Components
The remaining source modules contain:
- censor-aware discrete-hazard objectives;
- direct NetCVR, ranking, consistency, calibration, temporal, and expert-balance loss terms;
- deterministic training and environment-recording utilities;
- prospective beta and temperature calibration;
- binary discrimination and calibration metrics;
- rolling-window evaluation utilities;
- frozen-prediction delay-shift evaluation;
- moving-block resampling and multiple-comparison adjustment; and
- configuration loading, inheritance, and command-line utilities.
Configuration Files
The configs/ directory contains configuration files for:
- the primary chronological CASCADE workflow;
- component ablation studies;
- the complete ablation matrix;
- delayed-feedback perturbation analysis;
- the delay-shift condition matrix;
- MAC conversion-stage transfer evaluation; and
- ASOS GraphReturns return-stage compatibility evaluation.
The configurations define data locations, chronology rules, attribution windows, model structure, optimization settings, calibration settings, evaluation procedures, deterministic seeds, and output locations.
Data Documentation
The data/ directory contains:
- README.md, which describes how the public CASCADE, MAC, and ASOS GraphReturns resources are registered locally; and
- sources.yaml, which records the role, public source location, expected local directory, and data-handling status of each resource.
Raw source data are intentionally excluded from the repository. The package expects externally obtained public resources to remain outside version control and to be registered through file hashes before processing.
Documentation
The docs/ directory contains:
- ANONYMOUS_REVIEW.md — anonymous-review and repository-sanitization checklist;
- COMPUTE.md — compute environment and model-capacity description;
- DATA_DICTIONARY.md — canonical field definitions and prepared-data schema;
- REPRODUCIBILITY.md — determinism, chronology, label maturity, calibration, held-out evaluation, and external-stage protocol;
- RESULT_TRACEABILITY.md — mapping between study components, configurations, and structured record files; and
- RUNBOOK.md — ordered workflow for environment preparation, data registration, chronological preprocessing, model execution, controlled studies, and record reconstruction.
Scripts
The scripts/ directory contains the following command-line utilities:
Script	Included function
_common.py	Shared script helpers and path handling
fetch_resources.py	Public-resource registration and acquisition support
prepare_data.py	Chronological preprocessing, maturity derivation, shard creation, and hash registration
train.py	Fixed-seed CenCaM-Net training
calibrate.py	Prospective probability-calibrator fitting
evaluate.py	Checkpoint evaluation without parameter updates
evaluate_delay_shift.py	Frozen-prediction evaluation under delayed-feedback perturbations
run_all.py	Launching fixed-seed runs and controlled variants
build_reference_records.py	Reconstruction of immutable manuscript-aligned record files
verify_repository.py	Repository structure, manifest, configuration, and anonymity checks
package_archive.py	Deterministic construction of the anonymous-review archive


Manifests
The manifests/ directory contains:
- the canonical dataset contract;
- the chronological split schedule;
- the raw-resource hash registry;
- the repository file manifest; and
- metadata used to verify archive completeness and integrity.
Structured Records
The records/ directory contains machine-readable CSV and JSONL files organized into:
- primary CASCADE summaries;
- protocol diagnostics;
- baseline and ablation summaries;
- calibration and objective-selection records;
- rolling-window and attribution-window records;
- delay-shift, drift, and robustness records;
- statistical and block-sensitivity records;
- computational-profile and routing records; and
- MAC and ASOS external-stage records.
These files are accompanied by a record manifest that identifies their paths and integrity metadata.
Tests
The tests/ directory contains automated checks for:
- configuration inheritance and resolution;
- chronological history construction;
- label-maturity and streaming behavior;
- split and leakage guards;
- model input and output shapes;
- calibration components;
- evaluation metrics;
- statistical utilities; and
- deterministic protocol behavior.
Repository Scope
This package is limited to the materials required to inspect and reproduce the implemented workflow. It contains no author-identifying information, manuscript correspondence, redistributed raw records, authentication material, private links, or unpublished checkpoints.
