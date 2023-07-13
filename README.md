# Docking of anti-IL8 scFv to IL8

## Note on protein models

The model for the anti-IL8 scFv is taken from our [scFv-Modelling](https://github.com/iGEMIISc/scFv-Modelling) repository. In particular, we have chosen the ColabFold model generated with PDB70.

The model for IL8 is taken from the [PDB](https://www.rcsb.org/structure/2IL8) (PDB ID: 2IL8). This PDB file consists of 30 models, each with a different conformation of IL8. We have chosen the first model for our docking.

## Global Range Molecular Matching (GRAMM)

GRAMM is a docking web server that maps the intermolecular energy landscape by predicting a spectrum of docking poses corresponding to stable (deep energy minima) and transient (shallow minima) protein interactions. We used the anti-IL8 scFv as the receptor and IL8 as the ligand.

### Free Docking

In a free docking algorithm, a large number of conformations of the two proteins are evaluated to minimize the energy of their interaction. 

<img src="https://github.com/iGEMIISc/Docking-scFv-IL8/blob/master/GRAMM%20FreeDocking/model1.gif?raw=true">

### Template-based Docking

In the template-based method, a search is made from the PDB to identify heterodimer templates for our target. Then, homology modeling is used to map the target sequence onto the template structure.

<img src="https://github.com/iGEMIISc/Docking-scFv-IL8/blob/master/GRAMM%20Docking%20With%20Template/model1.gif?raw=true">

We will be taking the top models from both the free docking and template-based docking methods for further analysis. It should be noted that these can not be directly compared as the free docking method results are expressed in terms of shape complementarity while the template-based docking method results are expressed in terms of AACE18 (atomic contact energy) scores.

### Citations

1. Katchalski-Katzir, E., Shariv, I., Eisenstein, M., Friesem, A.A., Aflalo, C., Vakser, I.A., 1992, Molecular surface recognition: Determination of geometric fit between proteins and their ligands by correlation techniques, Proc. Natl. Acad. Sci. USA, 89:2195-2199.
2. Vakser, I.A., 1996, Long-distance potentials: An approach to the multiple-minima problem in ligand-receptor interaction, Protein Eng., 9:37-41.
3. Porter, K. A., Desta, I., Kozakov, D., & Vajda, S. (2019). What method to use for protein–protein docking? Current Opinion in Structural Biology, 55, 1–7.

## Analysis of Docking Results using PRODIGY

PRODIGY (PROtein binDIng enerGY prediction) is a web server for predicting the binding affinity of protein-protein complexes. We used this tool to analyze the docking results obtained from GRAMM.

| Method |  Predicted Binding Affinity <br> $\Delta G$ in $\text{kcal}~\text{mol}^{-1}$ | Predicted Dissociation Constant <br> $K_d$ in $\text{M}$ at $36 \degree\text{C}$ |
| :---: | :---: | :---: |
| Free Docking | $-16.5$ | $2.2 \times 10^{-12}$ |
| Template-based Docking | $-7.4$ | $6.3 \times 10^{-6}$ |

The calculations are done for $36 \degree\text{C}$ as this is the temperature at which our antibody will interact with IL8 in the human peritoneum*. It can be seen that free docking has provided a much more favorable binding affinity and dissociation constant than template-based docking. This suggests that the free docking could access a more stable conformation of the complex, and thus is more likely to be closer to the actual binding conformation.

Detailed results are available in the `PRODIGY` directory.

### Citations

1. Vangone A. and Bonvin A.M.J.J. "Contact-based prediction of binding affinity in protein-protein complexes", eLife, 4, e07454 (2015).
2. Xue L., Rodrigues J., Kastritis P., Bonvin A.M.J.J.*, Vangone A.*, "PRODIGY: a web-server for predicting the binding affinity in protein-protein complexes", Bioinformatics, doi:10.1093/bioinformatics/btw514 (2016).

### Other References

1. *Ott, D.E. The peritoneum and the pneumoperitoneum: a review to improve clinical outcome. Gynecol Surg 1, 101–106 (2004). https://doi.org/10.1007/s10397-004-0019-y
2. [Study](https://onlinelibrary.wiley.com/doi/10.1002/prot.25889) showing that GRAMM can successfully predict protein-protein interactions even for models of varying accuracy.
3. [Study](https://onlinelibrary.wiley.com/doi/10.1002/prot.25380) indicating the effectiveness of GRAMM, and ranking it among the top performers in some CAPRI rounds.

### Credits
We would like to thank [Amar Singh](https://compbio.ku.edu/people/amar-singh) from the Center for Computational Biology at the University of Kansas for answering our queries regarding the use of GRAMM, particularly with respect to the evaluation of the docking results. 
