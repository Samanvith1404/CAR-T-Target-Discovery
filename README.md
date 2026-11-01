# CAR-T Target Discovery

A research code-and-data package for CAR-T target discovery, clinical-trial mining, target evidence enrichment, construct/patent extraction, and binder-design experiments.

> **Reproducibility notice:** This repository is an organized snapshot of the supplied `.py` and `.csv` files. It is not yet a verified end-to-end release. Scripts may depend on local paths, datasets not included here, API credentials, model checkpoints, GPU/CUDA, external databases, or packages not captured in the source archive. Do not interpret the presence of a result CSV as proof that the associated pipeline can be rerun from this repository alone.

## Repository layout

- `src/stage1/` — Stage-1 target discovery, feature engineering, data preparation, training, diagnostics.
- `src/clinical_trials/` — ClinicalTrials.gov / ICTRP collection, classification, and enrichment.
- `src/construct_patents/` — CAR construct, antigen, patent, and sequence extraction utilities.
- `src/binder_design/` — ESM2 fine-tuning, Stage-2 models, and specificity-search scripts.
- `src/upstream_cartar/` — upstream CARTAR-related preprocessing scripts supplied in the archive.
- `data/source/` — source/reference datasets.
- `data/processed/` — intermediate and derived tables.
- `data/results/` — model outputs, trial extracts, validation results, and reports.
- `data/reference/` — candidate lists and external reference tables.
- `docs/` — inventory and notes.

## Suggested execution order (provisional)

1. Review source datasets and configure paths/API access.
2. Run clinical-trial collection and parsing scripts if refreshing trial data.
3. Prepare target and expression tables with the Stage-1 data/feature scripts.
4. Run `train_stage1.py` only after confirming its expected input paths and label definitions.
5. Prepare sequence/affinity pairs before running ESM2 fine-tuning or Stage-2 scripts.
6. Run binder-specificity/Boltz workflows only after installing their external tools and model dependencies.

The exact dependency graph and command-line arguments have **not** been validated in this packaging step. Inspect each script's `__main__` block and input paths before execution.

## Data provenance and citation

Preserve the original source citations, licenses, and access conditions for every external dataset. In particular, upstream CARTAR-derived scripts/data should retain attribution to the original project and its publication. Check each source provider's terms before redistributing data publicly. Do not upload patient-level, restricted, proprietary, or otherwise non-redistributable data.

## Security

Do not commit API keys, access tokens, passwords, private keys, or credentials. Keep secrets in environment variables or a local `.env` file, and never commit `.env`.

## Before publishing

- Verify all source-data licenses and redistribution permissions.
- Remove private, restricted, or sensitive records.
- Review scripts for hard-coded local paths and credentials.
- Add a tested `requirements.txt` or environment file after checking imports and versions.
- Re-run the pipeline from a clean environment and document exact commands.
- Add a license only if you have the rights to license all included code and data.

## File inventory

See `docs/FILE_INVENTORY.csv` for the original filename, packaged path, size, category, and SHA-256 checksum.
