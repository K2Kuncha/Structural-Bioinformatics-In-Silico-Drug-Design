# SOP 3: Homology Modeling & Validation

### 🧬 Background
When an experimentally determined X-ray crystallography structure is unavailable for a target protein, its 3D structure must be predicted computationally based on the known structure of a closely related homologous protein.

### 🛠️ Workflow Steps

**1. Template Identification**
* Input the target's FASTA sequence into **BLASTp** against the PDB database to find a homologous template with high sequence identity (typically >30%).

**2. Structure Prediction (Swiss-Model / Phyre2)**
* Submit the target sequence and the chosen template to the **Swiss-Model** or **Phyre2** automated modeling servers.
* The server will thread the target sequence over the template's backbone and perform energy minimization to generate a `.pdb` model.

**3. Model Validation (Ramachandran Plot)**
* Upload the predicted `.pdb` file to the **RAMPAGE** server.
* Analyze the resulting Ramachandran plot to ensure the majority of amino acid phi/psi dihedral angles fall within the "Favored" and "Allowed" regions, confirming a stereochemically valid protein fold.
