# Build notes - Synthetic Biology & Genetic Circuits

Repo2RLEnv pr_diff (v0.9.6), Harbor-format output. Domain: synthetic-biology.

## Funnel

| Stage | Count |
|---|---|
| Domain candidates (deduped) | 182 |
| After active+star+noise filter | 41 |
| Final target list (cap unlimited) | 41 |
| Repos with >=1 task | 3 |
| Repos with 0 tasks | 34 |
| Total tasks (unlimited (no per-repo cap)) | 189 |

## Generation

- Shared task bank: each repo generated once (pr_diff, limit=3,
  max_files_per_pr=15, min_loc_changed=2), 4-way concurrency,
  rate-limit-aware with .done checkpoint resume.
- Per-domain consolidation: rank by reward_calibration.loc_changed desc,
  keep ALL qualifying tasks (no per-repo cap). Zero-yield repos are NOT fabricated.
- Overlap with the 3 published cancer editions is allowed (user decision);
  domains are independent selections, not a partition of one repo set.

## Zero-yield repos (informational, 34)

- thunlp/GNNPapers
- PyO3/pyo3
- google-deepmind/alphafold
- github/gh-ost
- aimacode/aima-python
- nomi-sec/PoC-in-GitHub
- gepa-ai/gepa
- zouzhekang/YJYpaper
- QData/TextAttack
- cirosantilli/china-dictatorship
- thomasahle/sunfish
- nesaorg/nesa
- wcventure/FuzzingPaper
- EMI-Group/evox
- codeplea/genann
- Gforcex/OpenGraphic
- bebop/poly
- Edinburgh-Genome-Foundry/DnaFeaturesViewer
- Lattice-Automation/seqviz
- Edinburgh-Genome-Foundry/DnaChisel
- SysBioChalmers/RAVEN
- ctSkennerton/minced
- RicardoGEsteves/omniscient
- khokao/synergetica
- Russel88/CRISPRCasTyper
- seek4science/seek
- SynBioHub/synbiohub
- mckennalab/FlashFry
- synthego-open/ice
- cnapy-org/CNApy
- MyersResearchGroup/iBioSim
- Edinburgh-Genome-Foundry/DnaCauldron
- nf-core/crisprseq
- jvogan/motif

## Caveats

- Static validation only; real grading needs an LLM judge key + Docker.
- inline_dockerfile mode skips image build (no Docker daemon needed to publish).
- Provider secrets in upstream diffs were redacted before public release.
