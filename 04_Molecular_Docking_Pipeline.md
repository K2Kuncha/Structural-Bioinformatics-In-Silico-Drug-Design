# SOP 4: Molecular Docking & Drug Design

### 🧬 Background
Molecular docking is an *in silico* simulation used to predict the preferred orientation and binding affinity of a small molecule (ligand/drug) to a protein target when bound to each other to form a stable complex.

### 🛠️ Workflow Steps (ArgusLab / Discovery Studio)

**1. Macromolecule Preparation**
* Open the target protein (e.g., HIV-1 Protease, PDB: `1W5X`) in **Discovery Studio**.
* Remove water molecules and heteroatoms from the crystal structure.
* Identify the binding pocket and define it as the "Active Site".

**2. Ligand Preparation (ArgusLab)**
* Import the antiviral ligand molecule into **ArgusLab**.
* Click **"Add Hydrogen"** to complete the molecule's valency.
* Click **"Clean Geometry"** to perform a quick energy minimization of the ligand.
* Using the Molecule Tree View, define the molecule as a "Ligand" group.

**3. Docking Simulation & Scoring**
* Select the "Dock a Ligand" calculation.
* Execute the docking run. The software evaluates thousands of binding poses and calculates the binding energy for each.
* *Example Result:* Successfully simulated docking with a calculated pose energy (Docking Score) of **-6.6 kcal/mol**.

**4. Interaction Analysis**
* Re-import the docked complex into Discovery Studio.
* Generate a 2D interaction map to visualize Hydrogen bonds, Pi-Anion, and Amide-Pi interactions between the ligand and specific target residues (e.g., interactions with Asp25 in the protease active site).
