## Important notes

* Somehow our pipeliens had renamed `GCA_000001405.15` to `GCA_000001405.5`. We have manually fixed that in the latest version of the trees on **Nov 9, 2026**. 


|file | description| #nodes | #leaves | #species | branch lengths | inner labels |
|---|---|---:|---:|---:|---:|---:|
| [astralpro.l6.tre](./astralpro.l6.tre) | ASTRAL-Pro tree as inferred | 1127 | 564 | 561 | substitution unit | [localPP support](doi.org/10.1093/molbev/msw079) |



### The ASTRAL-Pro tree

* We include all 577 genomes present in the Cactus ([hal file](<https://genomeark.s3.amazonaws.com/index.html?prefix=downstream_analyses/genome_alignments/cactus/577way/>)) alignment (including duplicate human and mice), but we remove 13 invertebrate outgroups that had low representation in the alignment. 

* See [./annotations.tsv](annotations.tsv) for genome annotations.

* A total of 162,243 multi-copy loci are selected from the Cactus alignment using our in-house script that *will be* made available at <https://github.com/VGP/vgp-phyloscripts>. We used version `0.1.59-dev-2026-05-18`. See [this other repository](https://github.com/VGP/vgp-trees/tree/main/phase-1-cactus/multicopy) for more details  

* Gene trees are inferred using IQ-TREE

* The species tree is inferred using ASTRAL-Pro-3. It differed from the [v0.0.0](../v0.0.0) ROADIES tree in 13 (2.3%) of its branches. See [this other repository](https://github.com/VGP/vgp-trees/tree/main/phase-1-cactus/multicopy) for
more details. These are the the changing nodes (labels from the [Cactus guide tree](../v0.0.0/vgp-577way.nwk)):
	* CoreLandbirdsAnc02, 
	* BirdsAnc4, 
	* LaridaeAnc4, 
	* CoreWaterbirdsAnc02, 
	* ColumbeaAnc0, 
	* NeobatrachiaHyloideaAnc2, 
	* RayFinnedFishesAnc11, 
	* RayFinnedFishesAnc21, 
	* CichlidaeAnc2, 
	* ScombridaeAnc2, 
	* RayFinnedFishesAnc57, 
	* CartilaginousFishesAnc2, (**Shark monophyly**)
	* CartilaginousFishesAnc6

