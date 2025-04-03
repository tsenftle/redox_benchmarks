# README: Organization of Input, Output, and Optimized Structures

This directory contains quantum chemistry and DFT calculations organized by the level of theory and solvent model. The main folders represent different computational approaches and methods used in the study:

## **Main Directories**

1. **ORCA_6.0.0_SMD**  
2. **ORCA_6.0.0_COSMORS**  
3. **VASPsol_PAW-PBE**  
4. **VASPsol_PAW-r2SCAN**  
5. **VASPsol++_PAW-PBE**  
6. **VASPsol++_PAW-r2SCAN**  

Each of these directories contains subfolders organized by molecular codes (001, 002, 003, ... 188), representing individual molecules. Within each molecule's folder, the calculations are further divided into oxidation states:

- **ox** (oxidized state)
- **red** (reduced state)

---

## **Folder Structure and Contents**

### **ORCA_6.0.0_SMD**
This directory contains calculations performed using ORCA 6.0.0 with the SMD solvation model. The structure within each molecule's oxidized (`ox`) or reduced (`red`) folder is as follows:

- **`cs_rporg_XXX_ox_opt_01`**  
  - Optimization and frequency calculations.
  - Files: `.inp` (input file), `.out` (output log), and `.xyz` (optimized equilibrium structure).

- **`cs_rporg_XXX_ox_solv_01`** to **`cs_rporg_XXX_ox_solv_05`**  
  - Solvent-phase single-point energy calculations.
  - The suffix (`01` to `05`) represents the level of theory:
    - **05**: PBE0/aug-cc-pVTZ
    - **04**: r2SCANh/aug-cc-pVTZ
    - **03**: r2SCAN/aug-cc-pVTZ
    - **02**: B3LYP/aug-cc-pVTZ
    - **01**: TPSSh/aug-cc-pVTZ  
  - Files: `.inp` and `.out` for each level of theory.

### **ORCA_6.0.0_COSMORS**
This directory contains single-point energy calculations using the COSMORS solvation model. The folder structure is the same as ORCA_6.0.0_SMD, with molecular codes and oxidation states.

- Files: `.inp` and `.out` for each calculation.
- **Geometries**: The initial geometries for these calculations are obtained from the optimized `.xyz` structures in the `ORCA_6.0.0_SMD` directory.

### **VASPsol_PAW-PBE, VASPsol_PAW-r2SCAN, VASPsol++_PAW-PBE, VASPsol++_PAW-r2SCAN**
These directories contain VASP calculations using different solvation methods (`VASPsol` or `VASPsol++`) and exchange-correlation functionals (`PAW-PBE` or `PAW-r2SCAN`).

Each molecule’s subfolder follows the same structure as the ORCA directories:
- **ox/** (oxidized state)
- **red/** (reduced state)

Each oxidation state folder contains:
- **`INCAR`** - Input parameters for the VASP calculation.
- **`OUTCAR`** - Output log containing results.
- **`CONTCAR`** - Optimized structure from the VASP calculation.

---

## **Summary of Methodology**
- ORCA calculations are performed with SMD and COSMORS solvation models, optimizing structures and computing single-point energies at multiple levels of theory.
- VASP calculations are conducted using implicit solvent models (`VASPsol` and `VASPsol++`) and different functionals (`PAW-PBE` and `PAW-r2SCAN`).

---

## **Reference to Manuscript**
-The data presented in this repository corresponds to the manuscript with DOI: (currently under review) .
