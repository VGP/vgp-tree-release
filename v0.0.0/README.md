|file | description| #nodes | #leaves | #dichotomies | branch lengths | inner labels |
|---|---|---:|---:|---:|---:|---:|
| [roadies_v1.1.16b.nwk](./roadies_v1.1.16b.nwk) | ROADIES tree, as inferred, including all 581 species | 1161 | 581 | 580 |substitution unit | [localPP support](doi.org/10.1093/molbev/msw079) |
| [vgp-577way.nwk](vgp-577way.nwk) | Cactus guide tree, excludes 6 large genomes, adds a second human and mouse, and renames one. See below| 1153 | 577 | 576 | substitution unit | Cactus Node names |


### [roadies_v1.1.16b.nwk](./roadies_v1.1.16b.nwk) 

This is the tree inferred by [ROADIES](https://turakhia.ucsd.edu/ROADIES/). 

*  We sampled gene trees by running ROADIES in its deep mode in four stages:

	1. Full dataset (581 species): We sampled 128,000 loci across all species, which produced 29,239 gene trees after filtration steps.
	2. Bird-focused subset (139 species: 137 birds + 2 crocodiles as outgroups): Since avian phylogeny is particularly complex and requires a large number of gene trees to be correctly resolved, we increased the sampling depth, generating 54,288 gene trees after filtration steps, from 64,000 sampled loci. 
	3. Shark-focused run (partitioned dataset): To confidently resolve the relative placement of sharks compared to fishes and other vertebrates, we partitioned the dataset into three clades (sharks, fishes, and all remaining species) and enabled ROADIES to sample 8,000 loci evenly across the three groups, resulting in 1,848 gene trees post-filtration.
	4. Fish-focused subset (181 species: 178 fishes + 3 Gymnophiona as outgroups): Given the challenges in resolving the deep divergence within fishes, we sampled 160,000 loci from this subset, which yielded 37,766 gene trees.

    **Total:** $29,239+54,288+1,848+37,766=123,141$ gene trees in total. These gene trees are provided in [another GitHub repo](https://github.com/VGP/vgp-trees/tree/main/phase-1).

* We set the `MIN_ALIGN` to 10% of the number of input genomes for all partitions except for the bird-focused subset, where we set this parameter to 4. All other parameters were set to their default settings.


* This tree is the result of a constrained search, with a constrained tree, given in [./start.tre](start.tre). The start tree forced some resolutions that the unconstrained tree was getting wrong. 
	* The gene trees were inferred with no constraints. To obtain the final species tree, we used [./start.tre](start.tre) (depicted in [./start.pdf](start.pdf)) as a fixed starting tree constraint `--constraint ` as input to ASTRAL-Pro3:

	~~~bash
	astral-pro3 -t 64 --constraint starting.tre -i gene_trees_v1.1.9.nwk -o roadies_v1.1.14.nwk 
	~~~
	
	* This unrooted tree was manually rooted at the common ancestor of Echinodermata and Hemichordata (`GCF_902459465.1` and `GCA_040954625.2`)

	~~~bash
	cat roadies_v1.1.14.nwk |nw_reroot - GCF_902459465.1 GCA_040954625.2 > roadies_v1.1.15.nwk
	~~~
	* Branch lengths and support values were recomputed on this rerooted tree using
 
	~~~bash
	astral-pro3 -t 64 -C -c roadies_v1.1.15.nwk  -i gene_trees_v1.1.9.nwk -o roadies_v1.1.16a.nwk
	~~~

* astral-pro3 cannot infer the position and length of the root branch. We manually copied the branch lengths of the `GCF_902459465.1` and `GCA_040954625.2` and the common ancestor from `roadies_v1.1.14.nwk` onto `roadies_v1.1.16a.nwk` to obtain the final tree `roadies_v1.1.16b.nwk`. 

* Support values on the species tree are between 0 and 1. Above 0.95 is traditionally considered high. Below 0.8 is considered low. 
* Branch lengths are in units of the expected number of substitutions per site. 
	* Note that the root branch length included the manual adjustment noted above and is arbitrarily rooted at its middle point.  In general, branch lengths among invertebrates and the branches connecting vertebrates and non-vertebrates should be taken with a grain of salt, given the low gene sampling among invertebrates.  


* See [annotations.tsv](annotations.tsv) for an annotation file. 
	* `GCA_049190665.1` had the wrong label initially (salamanderfish). This genome was later suppressed and replaced with a proper arrowtail genome.

### [vgp-577way.nwk](vgp-577way.nwk)

Starting from  `roadies_v1.1.16b.nwk`, we

 * Dropped 6 large genomes that didn't make it to Cactus:(`GCA_026652325.1`, `GCA_036971685.2`, `GCA_040939525.1`, `GCA_964204655.1`, `GCA_964261635.1`, `GCA_964263255.1`, `GCF_040938575.1`),
 * Added a second human (`GCA_000001405.15`) and mouse (`GCA_000001635.9`). 
 * Renamed `GCA_036971685.2` to `GCF_037038585.1` because after creating the ROADIES tree, it was determined that the latter was a better assembly.
 * Gave names to all the animals (internal nodes, really!).