# 📁 Geoopt1234-xtbopt Database Structure
## Repository Organization
```Geoopt1234-xtbopt/
├── Benchmarks/ # Proof-of-concept giants (e.g., [36]CPP)
├── Methodology/ # Standards & protocols
├── Miscellaneous/ # Other interesting molecules
├── Scripts/ # Python/bash tools for validation
└── WHO EML 24th List (2025)/ # WHO Essential Medicines
```
## Per-Molecule Organization (this is applied for all molecules)
```
[Molecule_Name]
├── Input.sdf
├── Input_InChI.sdf
├── [SOLVENT]_[NETCHARGE]_[ETEMP]_[UHF]-pH7.4/
│ ├── Command.txt # Exact xtb command used
│ ├── xtbopt.sdf # Optimized geometry
│ ├── InChI.txt # Generated from final structure
├── [SOLVENT]\_[NETCHARGE]\_[ETEMP]\_[UHF]-pH7.4/
...
```
## File Storage Policy
- **GitHub:** Only files < 10MB (`.sdf`, `.txt`, `.md`)
- **Zenodo:** All large files (`.log`, `.hessian`, `.out`)
