# 📁 Geoopt1234-xtbopt Database Structure
## Repository Organization
```Geoopt1234-xtbopt/
├── Methodology/ # Standards & protocols
├── Benchmarks/ # Proof-of-concept giants (e.g., [36]CPP)
├── Drugs_WHO_Essential/ # WHO Essential Medicines
├── Miscellaneous/ # Other interesting molecules
└── scripts/ # Python/bash tools for validation
```
## Per-Molecule Organization (this is applied for all molecules)
```
[Molecule_Name]
├── INPUT.sdf
├── [SOLVENT]_[NETCHARGE]_[ETEMP]_[UHF]-pH7.4/
│ ├── COMMAND.txt # Exact xtb command used
│ ├──  xtbopt.sdf # Optimized geometry
│ ├── INCHI.txt # Generated from final structure
│ └── VALIDATION_REPORT.md # Pass/Fail quality check
├── [SOLVENT]\_[NETCHARGE]\_[ETEMP]\_[UHF]-pH7.4/
...
```
## File Storage Policy
- **GitHub:** Only files < 10MB (`.sdf`, `.txt`, `.md`)
- **Zenodo:** All large files (`.log`, `.hessian`, `.out`)
