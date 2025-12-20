# COMPUTATIONAL-THEORY-2025

SHA-256–focused notebook exercises aligned with FIPS 180-4. Written for an informed computing professional (e.g., a prospective employer) who expects minimal setup to run and review the work.

## Repository Layout
- `Problems.ipynb` — Single consolidated notebook containing Problems 1–5:
	- SHA-256 primitives: Parity, Ch, Maj, Σ/σ functions (32-bit NumPy operations)
	- Prime generation and derivation of SHA-256 K constants (fractional cube-root bits) with FIPS verification
	- `block_parse(msg)` generator (padding + 512-bit block parsing)
	- `hash(current, block)` per SHA-256 compression (section 6.2.2)
	- Password-hash exploration and hardening discussion

## Prerequisites
- Python 3.10+ (tested on 3.11+)
- `pip`
- Recommended: virtual environment (`python -m venv .venv`)

## Quick Setup
```bash
git clone https://github.com/CianDickerHughes/COMPUTATIONAL-THEORY-2025.git
cd COMPUTATIONAL-THEORY-2025
python -m venv .venv
source .venv/bin/activate  # Windows: .venv\Scripts\activate
python -m pip install -U pip
python -m pip install numpy jupyter
```

## Running the Notebooks
**VS Code (recommended):**
1) Open the folder in VS Code.
2) Choose the `.venv` Python interpreter if prompted.
3) Open `Problems.ipynb` and run cells sequentially.

**Jupyter CLI:**
```bash
jupyter lab    # or: jupyter notebook
# Open Problems.ipynb and run all cells
```

The consolidated notebook is self-contained; cells define required functions before they are used.

## Notes on Data and Reproducibility
- No large data files are required or stored in the repo.
- All computations are deterministic and rely only on NumPy.

## Problem Highlights
- **Problem 1:** Implement SHA-256 primitives (`Parity`, `Ch`, `Maj`, `Sigma0`, `Sigma1`, `sigma0`, `sigma1`) with 32-bit ops.
- **Problem 2:** Generate first 64 primes; compute cube-root fractional parts; extract 32-bit words; format as hex; verify against FIPS K constants.
- **Problem 3:** Implement `block_parse(msg)` to apply SHA-256 padding and emit 512-bit blocks per sections 5.1.1 and 5.2.1.
- **Problem 4:** Implement `hash(current, block)` to perform one SHA-256 compression step.
- **Problem 5:** Recover plaintexts for given SHA-256 hashes and discuss stronger password hashing (salting, key stretching/KDFs like PBKDF2, scrypt, Argon2, throttling).

problems [assessment/problems.md](assessment/problems.md).

## Reference
- Secure Hash Standard (FIPS 180-4): https://nvlpubs.nist.gov/nistpubs/FIPS/NIST.FIPS.180-4.pdf
- UTF-8 (Unicode Transformation Format – 8-bit) https://en.wikipedia.org/wiki/UTF-8
- Bytes Objects (immutable bytes) https://realpython.com/python-bytes/
- Generators (on-demand iteration) https://realpython.com/introduction-to-python-generators/

## Troubleshooting
- If VS Code cannot find the kernel, ensure the `.venv` interpreter is selected and run `python -m pip install jupyter` inside the environment.
- If NumPy import fails, reinstall: `python -m pip install --force-reinstall numpy`.
