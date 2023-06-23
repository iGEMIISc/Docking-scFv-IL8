# Docking of anti-IL8 scFv to IL8

## Note on protein models

The model for the anti-IL8 scFv is taken from our [scFv-Modelling](https://github.com/iGEMIISc/scFv-Modelling) repository. In particular, we have chosen the ColabFold model generated with PDB70.

The model for IL8 is taken from the [PDB](https://www.rcsb.org/structure/2IL8) (PDB ID: 2IL8). This PDB file consists of 30 models, each with a different conformation of IL8. We have chosen the first model for our docking.

## Global Range Molecular Matching (GRAMM)

GRAMM is a docking web server that maps the intermolecular energy landscape by predicting a spectrum of docking poses corresponding to stable (deep energy minima) and transient (shallow minima) protein interactions. We used the anti-IL8 scFv as the receptor and IL8 as the ligand.

### Free Docking

In a free docking algorithm, a large number of conformations of the two proteins are evaluated to minimize the energy of their interaction. By doing this, GRAMM provided us a docking with an energy of 

### Template-based Docking

In the template-based method, a search is made from the PDB to identify heterodimer templates for our target. Then, homology modeling is used to map the target sequence onto the template structure.

<img src="https://">

### Citations

1. Katchalski-Katzir, E., Shariv, I., Eisenstein, M., Friesem, A.A., Aflalo, C., Vakser, I.A., 1992, Molecular surface recognition: Determination of geometric fit between proteins and their ligands by correlation techniques, Proc. Natl. Acad. Sci. USA, 89:2195-2199.
2. Vakser, I.A., 1996, Long-distance potentials: An approach to the multiple-minima problem in ligand-receptor interaction, Protein Eng., 9:37-41.
3. Porter, K. A., Desta, I., Kozakov, D., & Vajda, S. (2019). What method to use for protein–protein docking? Current Opinion in Structural Biology, 55, 1–7.