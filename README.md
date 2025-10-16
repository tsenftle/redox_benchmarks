# README: Organization of Input, Output, and Optimized Structures

This directory contains quantum chemistry and DFT calculations organized by the level of theory, solvation model, and validation purpose. The main folders represent different computational approaches and datasets used in the study.

## **Main Directories**

1. **ORCA_6.0.0_SMD**  
2. **ORCA_6.0.0_COSMORS**  
3. **VASPsol_PAW-PBE**  
4. **VASPsol_PAW-r2SCAN**  
5. **VASPsol++_PAW-PBE**  
6. **VASPsol++_PAW-r2SCAN**  
7. **VASPsol_PAW-HSE06_sp**  
8. **VASPsol++_PAW-HSE06_sp**  
9. **VASPsol_PAW-HSE06_full_opt**  
10. **Benchmark_tests**  
11. **Water**

Each of these directories contains subfolders organized by molecular codes (001, 002, 003, ... 188), representing individual molecules or test systems. Within each molecule’s folder, the calculations are further divided into oxidation states:

- **ox** (oxidized state)  
- **red** (reduced state)

---

## **Folder Structure and Contents**

### **ORCA_6.0.0_SMD**  
This directory contains calculations performed using ORCA 6.0.0 with the SMD solvation model in MeCN.  
The structure within each molecule’s oxidized (`ox`) or reduced (`red`) folder is as follows:

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

---

### **ORCA_6.0.0_COSMORS**  
This directory contains single-point energy calculations using the COSMO-RS solvation model in MeCN.  
The folder structure is the same as ORCA_6.0.0_SMD, with molecular codes and oxidation states.

- Files: `.inp` and `.out` for each calculation.  
- **Geometries**: The initial geometries for these calculations are obtained from the optimized `.xyz` structures in the `ORCA_6.0.0_SMD` directory.

---

### **VASPsol_PAW-PBE, VASPsol_PAW-r2SCAN, VASPsol++_PAW-PBE, VASPsol++_PAW-r2SCAN**  
These directories contain VASP calculations carried out **in MeCN** using implicit solvation models (`VASPsol` or `VASPsol++`) and exchange–correlation functionals (`PAW-PBE` or `PAW-r2SCAN`).

Each molecule’s subfolder follows the same structure as the ORCA directories:  
- **ox/** (oxidized state)  
- **red/** (reduced state)  

Each oxidation state folder contains:  
- **`INCAR`** – Input parameters for the VASP calculation.  
- **`OUTCAR`** – Output log containing results.  
- **`CONTCAR`** – Optimized structure from the VASP calculation.

---

### **VASPsol_PAW-HSE06_sp and VASPsol++_PAW-HSE06_sp**  
These directories contain **single-point (sp)** calculations carried out **in MeCN** using the HSE06 hybrid functional within `VASPsol` and `VASPsol++`, respectively.  
- The single-point energies were computed using the **optimized geometries obtained at the corresponding PAW-PBE level**.  
- These calculations are used to evaluate the effect of hybrid functional corrections on electronic structure and redox potentials.

---

### **VASPsol_PAW-HSE06_full_opt**  
This directory contains **fully relaxed (full_opt)** calculations at the PAW-HSE06 level, carried out **in MeCN**.  
- These calculations serve as **validation examples**, comparing the results of full hybrid-functional relaxations against those obtained from single-point evaluations on PAW-PBE geometries.

---

### **Benchmark_tests**  
This directory contains **validation and benchmark tests** performed to ensure the consistency of both ORCA and VASP setups.  
- Includes representative **input (`.inp`, `INCAR`)** and **output (`.out`, `OUTCAR`)** files.  

---

### **Water**  
This directory contains **examples of selected molecules modeled in water** to test the translation of `VASPsol` and `VASPsol++` to **protic solvents**.  
- These examples illustrate the adaptability of both solvation models beyond MeCN.  
- The folder structure mirrors that of the MeCN datasets, with separate `ox` and `red` subdirectories for each molecule.  

---

## **Summary of Methodology**

- ORCA calculations were performed with the SMD and COSMO-RS solvation models in MeCN, optimizing structures and computing single-point energies at multiple levels of theory.  
- VASP calculations were carried out **in MeCN** using implicit solvent models (`VASPsol` and `VASPsol++`) and different exchange–correlation functionals (`PAW-PBE`, `PAW-r2SCAN`, `PAW-HSE06`).  
- Additional benchmark and solvent-transfer tests (in water) are provided for consistency validation and to demonstrate the broader applicability of the solvation models.  
- HSE06 datasets include both **single-point** and **fully relaxed** calculations for benchmarking consistency.

---

## **Reference to Manuscript**

- The data presented in this repository is distributed as part of the publication  
  **"Can reduction potentials be calculated with plane-wave density functional theory? Comparing the accuracy of VASPsol and VASPsol++ to SMD and COSMO-RS solvation methods."**  
- DOI: (currently under review).  
- Data gathered and prepared by **Christian Sandoval-Pauker**, Postdoctoral Fellow, Smalley-Curl Institute, Rice University, Houston, TX 77005.
