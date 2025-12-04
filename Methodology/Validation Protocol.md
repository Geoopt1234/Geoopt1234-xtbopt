# Validation Protocol
*Version 1.0 - All calculations must pass these checks*

## 🚨 Mandatory Checks (Automatic Rejection if Failed)

### 1. Convergence & Numerical Stability
- **Gradient Norm:** `< 0.00050 Eh/a₀` (from `xtb.out`)
- **Optimization:** Must converge **BEFORE** hitting `--cycle 10000` limit
- **SCF Cycles:** Must converge **BEFORE** hitting `--iterations 1000` limit

### 2. Frequency Validation  
- **Imaginary Frequencies:** `0` allowed (any negative Frequencies aren't allowed)

### 3. Chemical Identity Check
- **InChI Match:** InChI generated from `xtbopt.sdf` must match source InChI
  - ✅ **Pass:** Identical core connectivity AND stereo connectivity
  - ❌ **Fail:** Different molecular skeleton OR different stereo connectivity (automatic rejection)

### 4. File Compliance
- **GitHub Files:** .sdf Must be `< 10MB` each
- **Required Files:** `XTBOPT.sdf`, `INCHI.txt`, `COMMAND.txt`, `VALIDATION_REPORT.md`
- **Zenodo Archive:** Every technical must be archived with DOI

## ⚠️ Manual Review Required (Flags for Maintainer)
### Unusual Convergence Patterns
- Optimization taking `> 5000 cycles` (even if converged)
- SCF requiring `> 500 iterations` 
- May indicate problematic initial geometry
