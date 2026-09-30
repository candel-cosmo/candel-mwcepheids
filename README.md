# candel-mwcepheids

Milky Way Cepheid calibration model for CANDEL. A probe package for
[CANDEL](https://github.com/candel-cosmo/CANDEL), part of the
[candel-cosmo](https://github.com/candel-cosmo) organisation. It imports the
core `candel` library; the core never imports it. See the
[CANDEL README](https://github.com/candel-cosmo/CANDEL#how-the-repositories-fit-together)
for how the repositories fit together.

## What it provides

Forward model of the Gaia--HST Milky Way Cepheid period--luminosity
calibration, with selection effects, distance marginalisation and physical
(e.g. spiral-arm) priors (`model.which_run = "MWCepheids"`). Data preparation
lives in `scripts/preprocess/` and mock tests in `scripts/mocks/`.

## Install

Clone this repository next to the CANDEL core and install both, core first:

```bash
git clone https://github.com/candel-cosmo/CANDEL.git
git clone https://github.com/candel-cosmo/candel-mwcepheids.git
cd CANDEL
python -m venv venv_candel && source venv_candel/bin/activate
pip install -e .
pip install --no-deps -e ../candel-mwcepheids
```

Data, results and the machine-local `local_config.toml` live in the CANDEL
checkout. Python code finds it through the installed `candel`
(`candel.util.CANDEL_ROOT`); shell scripts use `$CANDEL_ROOT`, defaulting to
`../CANDEL`.

## Layout

- `candel_mwcepheids/` — the package
- `configs/` — run configurations
- `scripts/` — preprocessing, mocks and submission helpers
- `papers/` — scripts and notebooks behind each paper

## Papers

- `papers/MWCepheids/` — Forward-modelling Milky Way Cepheids, [arXiv:2603.09880](https://arxiv.org/abs/2603.09880)

## Run

```bash
python ../CANDEL/scripts/runs/main.py --config configs/config_MWCepheids.toml
```

Batch grids are defined in `candel_mwcepheids/specs.py` and built with the core's
`scripts/runs/generate_tasks.py`.

## License

MIT; see `LICENSE`.
