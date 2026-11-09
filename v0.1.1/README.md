## Please obtain the updated dated tree if you downloaded before Nov, 9, 2026
## Important notes


1. We first released a v0.1.1 dated tree, only to later find out that some calibration points could be improved. We then **released a second version of *the dated* tree on Nov, 9, 2026**, changing the name to `astralpro.l6p1.dated.round2`. The previous files are moved ot the `obsolete` folder. 
2. We dated the tree after eliminating the two non-vGP genomes (`GCA_000001405.15`, `GCA_000001635.9`) included in Cactus (and thus, our ASTARL tree) and re-estimating branch lengths. 
3. Somehow our pipelines had renamed `GCA_000001405.15` to `GCA_000001405.5`. We have manually fixed that in the latest version of the trees on **Nov 9, 2026**, keeping the old file under [./obsolete](obsolete). 

|file | description| #leaves | #species | branch lengths | inner labels |
|---|---|---:|---:|---:|---:|
| [astralpro.l6p1.tre](./astralpro.l6p1.tre) | ASTRAL-Pro tree plus kxProAnne1 (lungfish) | 565 | 561 | substitution unit | [localPP support](doi.org/10.1093/molbev/msw079) |
| [astralpro.l6p1.perspecies.tre](./astralpro.l6p1.perspecies.tre) | same as above, but eliminating the non-VGP human (`GCA_000001405.15`) and mouse genomes (`GCA_000001635.9`) | 563 | 561 | substitution unit | [localPP support](doi.org/10.1093/molbev/msw079) |
| [astralpro.l6p1.dated.round2.nwk](./astralpro.l6p1.dated.round2.nwk) | Dated ASTRAL-Pro tree plus kxProAnne1 (lungfish), dropping the two non-VGP genomes | 563 | 561 | time unit | None |
| [astralpro.l6p1.dated.round2.nexus](./astralpro.l6p1.dated.round2.nexus) | Dated ASTRAL-Pro tree plus kxProAnne1 (lungfish), dropping the two non-VGP genomes in **nexus** format | 563 | 561 | time unit | Multi-attreibute annotations, including date CIs|



### The ASTRAL-Pro tree

* We start from the dataset for [../v0.1.0](../v0.1.0) and add one more species, lungfish (kxProAnne1), which was missing from the Cactus using a LASTZ-based pipeline. Our pipeline found this species for 4350 loci. We redid gene trees and reran ASTRAL-Pro as v0.1.0. Then, we rerooted and ordered branches as shown below. 

	~~~bash
	nw_reroot -s astralpro.l6p1.tre GCF_030490865.1|nw_reroot -s - GCA_964187855.1 GCA_048934315.1 |nw_order -cn -
	~~~

* We dated using MD-Cat. See <https://github.com/VGP/vgp-dating/blob/main/dating/README.md>. 

* For genome name mappings, see [annotations.tsv](./annotations.tsv)

