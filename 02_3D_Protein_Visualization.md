# SOP 2: 3D Protein Structure Visualization

Once you have your target protein, inspecting its 3D structure helps you see where alpha-helices, beta-sheets, and potential drug-binding pockets actually sit in space—and whether a mutation is buried in the core or right on the active site.

---

### 1. Grabbing a High-Quality Structure (RCSB PDB)
* Search the **RCSB Protein Data Bank (PDB)** for an experimentally solved structure (X-ray crystallography, Cryo-EM, or NMR).
* **Quality check:** When multiple structures exist, pick one with high resolution (ideally **< 2.0 Å**), minimal missing loops, and a bound ligand if you want to see the active site in action.
* *Example:* Download PDB ID **`1W5X`** (HIV-1 Protease).

### 2. Visualizing the Structure (PyMOL / BIOVIA Discovery Studio)
1. Load the `.pdb` file into **PyMOL** (or **BIOVIA Discovery Studio**).
2. Switch the view from default `Lines` to **`Cartoon`** so secondary structures (helices, sheets, loops) are easy to read.
3. **Color by chain** to separate multi-subunit complexes (like the HIV-1 protease homodimer), or **color by secondary structure** to highlight structural motifs.
4. **Clean up the clutter:** Hide water molecules (`HOH`) unless they are known to mediate hydrogen bonding in the active site.
5. **Inspect the active site:** Select key catalytic residues (for HIV-1 protease, the `Asp25–Thr26–Gly27` catalytic triad) and display them as **`Sticks`** to inspect side-chain orientations and polar contacts.

### Quick Reproducible PyMOL Commands
Instead of clicking through menus every time, you can paste this straight into the PyMOL command line to fetch and style `1W5X` in seconds:

```python
fetch 1w5x
remove resn HOH
hide everything
show cartoon
util.cbc                                # Color by chain
select active_site, resi 25-27          # HIV-1 protease catalytic triad
show sticks, active_site
util.cbag active_site                   # Color active site by atom
zoom active_site, 8
```

Protein be like: Stop rotating me!!! I am dizzy!
