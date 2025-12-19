# Geoopt1234-xtbopt

A computational chemistry database of consistently optimized molecular geometries with complete calculation provenance.

## Data Structure

### GitHub Repository
This repository contains essential research data organized as:<br>
```
data/[Chemical Class]/[Molecule Name]/
├── [Molecule].sdf # Starting geometry
├── [Molecule]_InChI.txt # Chemical identity validation
└── [Molecule]_solvent_charge_temp_spin/
    ├── command.txt # Exact xtb command used
    ├── InChI.txt # Validation of optimized structure
    ├── xtbopt.sdf # Final optimized geometry
    └── Zenodo.txt # Link to complete calculation archive
```

### Zenodo Archives
Complete technical records (logs, hessians, frequencies, etc.) are archived on Zenodo in 50GB volumes. Each molecule's `Zenodo.txt` file contains a direct link to its specific archive volume.

## Usage

1. **Navigate** to a chemical class in `data/` (e.g., `WHO EML 24th List (2025)`)
2. **Select** a molecule folder
3. **Use** `xtbopt.sdf` for optimized geometries
4. **Reference** `command.txt` for calculation methodology
5. **Consult** `Zenodo.txt` for complete technical verification

## Calculation Protocol

All geometries are optimized using:
- `xtb` 6.7.1 with GFN2-xTB method
- ALPB implicit solvation (26 environments including vacuum)
- Extreme convergence criteria (`--ohess extreme --acc 0.0001 ---iterations 1000 --cycles 10000 -input gbsagrid=extreme --etemp 300 --gfn 2 -P 1 --strict` as a minimum requirement)
- Physiological protonation states at pH 7.4 (only for alkaloids and biology related molecules)

## Licensing

### Dual License Scheme

**Academic/Non-Commercial Use:**
- MIT License - Permissive use with attribution
- Covers research, education, and non-commercial applications<br>
See [LICENSE](https://github.com/Geoopt1234/Geoopt1234-xtbopt/blob/main/LICENSE)

**Commercial Use:**
- Alternative commercial license available upon request
- Contact for proprietary application terms
- All files including MOLECULE_InChI.txt, MOLECULE.sdf, and all files in solvent folders are completely in public domain according to CC0 1.0 Universal legal code
Complete license terms are in the `LICENSE` file in the repository root.<br>
See [LICENSE-CC0-FILES](https://github.com/Geoopt1234/Geoopt1234-xtbopt/blob/main/LICENSE-CC0-FILES)

## Citation

When using this database, cite both:
1. This GitHub repository
2. The relevant Zenodo archive volume(s) for reproducibility

## Verification

All structures undergo:
1. InChI matching between source and optimized geometries
2. Gradient norm convergence verification
3. Frequency validation (no imaginary frequencies)

Full verification data is accessible via Zenodo links in each molecule folder.

## Contributing

See `CONTRIBUTING.md` for molecule submission guidelines and quality standards.
