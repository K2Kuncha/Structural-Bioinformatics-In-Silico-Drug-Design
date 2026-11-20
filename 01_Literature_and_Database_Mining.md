# SOP 1: Target Validation & Sequence Retrieval

Before building a 3D model or running docking simulations, you need to make sure you're working with the right canonical protein sequence—and that you understand its known domains, active sites, and disease-relevant variants.

---

### 1. Quick Literature & Target Check
* Search **NCBI PubMed** using targeted Boolean queries (e.g., `("HIV-1 protease"[Title/Abstract]) AND ("inhibitor"[Title/Abstract] OR "resistance"[Title/Abstract])`) to check for recent crystal structures, known binding pockets, and clinically relevant mutations.
* Note any specific isoforms or mutated residues that matter for your downstream docking.

### 2. Fetching & Verifying the Sequence
1. Search for your target protein in **UniProtKB** (prefer reviewed **Swiss-Prot** entries over unreviewed TrEMBL entries to avoid annotation errors).
2. Check the **Family & Domains**, **Subcellular Location** (e.g., transmembrane regions), and **Pathology & Biotech** tabs to confirm which region of the protein you actually need to model.
3. Download the canonical amino acid sequence in **FASTA** format.
4. Cross-check against **NCBI Entrez / RefSeq** if you need to map the protein back to its underlying gene or transcript ID.

### Quick CLI Alternative (For Reproducible Pipelines)
Instead of clicking through the browser, you can pull a reviewed FASTA sequence directly from UniProt in one line (example using human *TP53*, accession `P04637`):

```bash
curl -s "[https://rest.uniprot.org/uniprotkb/P04637.fasta](https://rest.uniprot.org/uniprotkb/P04637.fasta)" -o P04637.fasta

### 3. Handling Mutations & Disease Variants
If you are modeling a specific genetic variant or studying how a mutation alters protein structure:
* **Nucleotide-level changes (indels, frameshifts, or complex variants):** Grab the coding sequence (CDS) from NCBI RefSeq, introduce the base change(s) directly, and translate the mutated DNA into an amino acid sequence (using a tool like **ExPASy Translate** or a quick Biopython script) before moving to modeling.
* **Simple missense mutations:** You can edit the target residue directly in the canonical protein FASTA file (e.g., swapping `R` to `H` at the affected position) and save it as a separate `mutant.fasta` file to compare against the wild-type model.
* *Quick tip:* Always double-check your residue numbering against the canonical UniProt sequence—PDB crystal structures sometimes omit signal peptides or disordered N-terminal regions, which can shift the numbering.
