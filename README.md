# COMPUTATIONAL-THEORY-2025

SHA-256–focused notebook exercises aligned with FIPS 180-4. Written for an informed computing professional (e.g., a prospective employer) who expects minimal setup to run and review the work.

## Repository Layout
- `problems/` — directory containing separate notebooks for each problem (problem1.ipynb … problem5.ipynb).
	- Each notebook is self-contained: helper functions for that problem are defined in cells at the top of the notebook where appropriate.
- Problem notebooks correspond to the sections previously combined in `Problems.ipynb` (SHA-256 primitives, K-constants, padding/parse, compression, passwords).

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
1) Open the folder in VS Code and select the `.venv` interpreter if prompted.
2) Open the notebook you want to run from the `problems/` folder (for example `problems/problem3.ipynb`).
3) To run only what's needed for a single problem: run the notebook's top helper cells (they define the functions used by later cells) then run the specific cells you want to evaluate. Use the editor buttons `Run Cell`, `Run Above`, or `Run Below` to limit execution.

**Jupyter CLI / Lab:**
```bash
jupyter lab    # or: jupyter notebook
# Open the desired file under problems/ (e.g. problems/problem2.ipynb)
```
- In Jupyter you can run individual cells or `Run > Run All Above` to execute helper definitions first, then run only the example/test cells for that problem.

Notes:
- Each problem notebook places its helper functions near the top so you can execute just those cells before running demonstrations or tests; you do not need to run all problems to inspect or run a single one.
- If you prefer automation, open the notebook and use `Kernel → Restart & Run All` to run the whole notebook end-to-end.

All-in-one notebook (root): If you want to see every problem run together, open `problems.ipynb` at the repository root (consolidated). It contains all helper functions and example/test cells; use `Kernel → Restart & Run All` to execute the full end-to-end workflow.

**Jupyter CLI:**
```bash
jupyter lab    # or: jupyter notebook
# Open problems.ipynb (repository root) and run all cells
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
- UTF-8: https://en.wikipedia.org/wiki/UTF-8
- Bytes Objects: https://realpython.com/python-bytes/
- Generators: https://realpython.com/introduction-to-python-generators/
- OWASP Password Storage Cheat Sheet: https://cheatsheetseries.owasp.org/cheatsheets/Password_Storage_Cheat_Sheet.html
- Prime numbers: https://www.geeksforgeeks.org/python/python-program-to-print-all-prime-numbers-in-an-interval/
- NumPy Bitwise Operations: https://numpy.org/doc/stable/reference/routines.bitwise.html
- BCrypt: https://pypi.org/project/bcrypt/
- Argon2 (NIST-recommended KDF): https://github.com/P-H-C/phc-winner-argon2

## Troubleshooting
- If VS Code cannot find the kernel, ensure the `.venv` interpreter is selected and run `python -m pip install jupyter` inside the environment.
- If NumPy import fails, reinstall: `python -m pip install --force-reinstall numpy`.
