# SOP 4: Molecular Docking & Interaction Analysis

Molecular docking simulates how a small molecule (ligand or drug candidate) fits into a protein's binding pocket and estimates how tightly it binds. Below is a straightforward GUI workflow using **BIOVIA Discovery Studio** and **ArgusLab** (using HIV-1 Protease, PDB: `1W5X`, as a worked example), followed by the command-line equivalent for automated runs.

---

### 1. Prepping the Target Protein (BIOVIA Discovery Studio)
1. Load the target structure (e.g., HIV-1 Protease, PDB: **`1W5X`**).
2. Strip out crystallographic water molecules (`HOH`) and non-essential heteroatoms so they don't artificially block the pocket.
3. Add polar hydrogens and define the binding pocket coordinates around the known active site.

### 2. Prepping the Ligand (ArgusLab)
1. Import your small-molecule ligand structure.
2. **Add hydrogens** to satisfy valency at physiological pH.
3. Run **Clean Geometry** (energy minimization) so the ligand starts in a realistic, low-energy 3D conformation rather than a flat 2D sketch.
4. Define the molecule as a `Ligand` group in the Molecule Tree View.

### 3. Running the Docking Simulation
* Run the **Dock a Ligand** calculation to sample binding poses within the active-site grid box and score their estimated binding free energy ($\Delta G$).
* **Example result:** Docking an antiviral candidate into `1W5X` yielded a top pose binding energy of **`-6.6 kcal/mol`**.
* *Validation tip:* Whenever possible, redock the protein's original co-crystallized ligand first—if the predicted pose overlays the crystal pose with an **RMSD less than 2.0 Å**, your grid box and parameters are reliable.

### 4. Inspecting Protein–Ligand Interactions
1. Open the top-scoring docked complex back in **BIOVIA Discovery Studio**.
2. Generate a **2D Interaction Diagram** to check whether the binding score is backed by real chemistry—specifically looking for **hydrogen bonds**, **Pi-Anion**, and **Amide-Pi** interactions with key catalytic residues (such as **`Asp25`** in the HIV-1 protease active site).

### AutoDock Vina
For screening multiple ligands reproducibly on Linux/HPC, the same workflow runs in one line using **AutoDock Vina** (after converting structures to `.pdbqt` via OpenBabel or Meeko):

```bash
vina --receptor 1w5x_clean.pdbqt \
     --ligand antiviral.pdbqt \
     --center_x 10.5 --center_y 22.0 --center_z 15.2 \
     --size_x 20 --size_y 20 --size_z 20 \
     --out docked_poses.pdbqt
```
Perfect fit never exists! 
