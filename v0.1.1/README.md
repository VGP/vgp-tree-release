|file | description| #nodes | #leaves | #dichotomies | branch lengths | inner labels |
|---|---|---:|---:|---:|---:|---:|
| [astralpro.l6p1.tre](./astralpro.l6p1.tre) | ASTRAL-Pro tree plus kxProAnne1 (lungfish)| 1129 | 565 | 564 | substitution unit | [localPP support](doi.org/10.1093/molbev/msw079) |



### The ASTRAL-Pro tree

* We start from the dataset for [../v0.1.0](../v0.1.0) and add one more species, lungfish (kxProAnne1), which was missing from the Cactus using a LASTZ-based pipeline. Our pipeline found this species for 4350 loci. We redid gene trees and reran ASTRAL-Pro as v0.1.0. Then, we rerooted and ordered branches as shown below. 

~~~bash
nw_reroot -s astralpro.l6p1.tre GCF_030490865.1|nw_reroot -s - GCA_964187855.1 GCA_048934315.1 |nw_order -cn -
~~~
