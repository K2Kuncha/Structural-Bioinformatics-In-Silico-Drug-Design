# SOP 2: 3D Protein Structure Visualization

### 🧬 Background
Understanding the spatial arrangement of amino acids (alpha-helices, beta-sheets) is critical for identifying potential drug-binding pockets.

### 🛠️ Workflow Steps

**1. Data Acquisition (RCSB PDB)**
* Query the **Protein Data Bank (PDB)** for experimentally determined structures (X-ray diffraction, NMR).
* *Example:* Retrieve PDB ID `1W5X` (HIV-1 Protease).

**2. Visualization via PyMOL / Discovery Studio**
* Import the `.pdb` file into **PyMOL** or **Accelrys Discovery Studio**.
* Change the visual representation from "Lines" to "Cartoon" or "Ribbon" to easily identify secondary structures.
* Color the structure by secondary structure type or by chain to differentiate multi-subunit complexes.
* **Active Site Identification:** Highlight specific residues known to be critical for the enzyme's catalytic function, altering their representation to "Sticks" to view side-chain orientations.
