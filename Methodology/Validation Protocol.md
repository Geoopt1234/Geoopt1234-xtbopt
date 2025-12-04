# Geoopt1234-xtbopt Validation Protocol
*Version 1.0 - All calculations must pass these checks*

## 🚨 Mandatory Checks (Automatic Rejection if Failed)

### 1. Convergence & Numerical Stability
- **Gradient Norm:** `< 0.001 Eh/a₀` (from `xtb.out`)
- **Optimization:** Must converge **BEFORE** hitting `--cycle 10000` limit
- **SCF Cycles:** Must converge **BEFORE** hitting `--iterations 1000` limit

### 2. Frequency Validation  
- **Imaginary Frequencies:** `0` allowed (tolerance: `> -20 cm⁻¹` for numerical noise)
- **Lowest Real Frequency:** Should be physically reasonable (e.g., `> 5 cm⁻¹` for rigid molecules)

### 3. Chemical Identity Check
- **InChI Match:** InChI generated from `XTBOPT.sdf` must match source InChI
  - ✅ **Pass:** Core connectivity identical (allow stereo variations for review)
  - ❌ **Fail:** Different molecular skeleton (automatic rejection)

### 4. File Compliance
- **GitHub Files:** Must be `< 10MB` each
- **Required Files:** `XTBOPT.xyz`, `INCHI.txt`, `COMMAND.txt`, `VALIDATION_REPORT.md`
- **Zenodo Archive:** Large files (`xtb.out`, `hessian`, `g98.out`) must be archived with DOI

## ⚠️ Manual Review Required (Flags for Maintainer)

### 1. Stereochemistry Changes
If InChI stereo layer differs:
- Is this a **physically possible** conformational change?
- Example: Flexible bond rotation ✅ vs. chiral center inversion ❌
- Decision by senior maintainer required

### 2. Unusual Convergence Patterns
- Optimization taking `> 5000 cycles` (even if converged)
- SCF requiring `> 500 iterations` 
- May indicate problematic initial geometry

## 🔧 The Validation Pipeline

All submissions run through `scripts/validate_submission.py`:

```bash
python scripts/validate_submission.py molecules/[Molecule_Name]/