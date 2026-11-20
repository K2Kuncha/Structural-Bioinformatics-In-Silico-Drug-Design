# SOP 3: Homology Modeling & Structure Validation

When there isn't an experimental X-ray or Cryo-EM structure in the PDB for your protein, you have to predict its 3D fold computationally. Classical homology modeling builds a structure using a closely related template protein—and validating the geometry afterward ensures you aren't docking a drug into a physically impossible fold.

Note: Before building a model from scratch, always check if a high-confidence prediction already exists in the **AlphaFold Protein Structure Database**, or run **ColabFold** for custom/mutated sequences.)

---

### 1. Finding a Good Template
* Run your target FASTA sequence through **BLASTp** against the **PDB** database.
* Look for a homologous template with **greater than 30% sequence identity** and strong query coverage—especially across the functional domain or active site you care about.

### 2. Building the 3D Model (SWISS-MODEL)
1. Upload your target sequence (and preferred template, if you want manual control) to **SWISS-MODEL** (or **Phyre2** for remote homologs).
2. The server aligns your sequence to the template backbone, models loop regions, and runs energy minimization to resolve major steric clashes.
3. Download the resulting `.pdb` model and check its **GMQE** and **QMEANDisCo** quality scores.

### 3. Validating the Fold (Ramachandran Plot)
Never trust a predicted structure blindly—check its stereochemical quality first:
1. Open your `.pdb` file in **SWISS-MODEL Structure Assessment** or upload it to **MolProbity**.
2. Inspect the **Ramachandran plot** (which maps backbone $\phi$ and $\psi$ dihedral angles):
   * Aim for **greater than 90–95% of residues** in the *Favored* region.
   * Check any *Outliers*—if an outlier is sitting in a floppy surface loop, it's usually fine; if it's right inside your active site, you'll need to refine the model or pick a better template.

---
May your Ramachandran plots be outlier-free and your steric clashes nonexistent.
