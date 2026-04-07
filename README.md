# Kodama
## 1. Advanced PCA by VCF and FASTA info
- Drop consensus fasta into ./cons and VCFs into ./vcf folders. Ensure they have the same name. 
- Execute the R script using

```
Rscript advance_PCA_ewa.r 
```

## 2. Beast
- Use the traits to now execute beast (10.5.0)
- Parameters:
- the way i structured it, BEAST outputs in /ephxz/quasi/19A/Beast. the quasispecies MCMC is in ./tree

### Tree annotator
> [!IMPORTANT]
> By default, with as many traits active, you might run into Java memory errors. You can manually find the treeannotator.jar and increase the memory allocation. Or edit the executable directly.
```
which treeannotator
nano [path]/treeannotator
```
Find the lines that have `-Xms64m -Xmx4096m` and modify the xmx to 8G or whatever that is appropriate. Then run treeannotator again normally
```
treeannotator -burnin 1000000 [in].trees.txt [out].tree
```
## 3. Transphylo and code


#WAIT
Dropping the descrete varaibles into beasta always pushed the tip dates. But the issues is generatlly speaking: that same effect is very likely to recur in the allele‑frequency route you’re now targeting, unless you explicitly constrain or calibrate the trait‑like component. The core issue is that continuous Brownian‑motion‑style traits (whether PCA scores or allele frequencies) pull the branch‑length / rate‑time balance, often pushing node dates “later” in shallow, fast‑evolving systems like SARS‑CoV‑2.

Key considerations:
Transmission bottleneck: only a small number of viral genomes (sometimes even one) passes from donor to recipient, sampling a subset of the donor’s quasispecies.

Founder effect: the recipient’s population is dominated by that subset, so allele frequencies can shift dramatically, even if the donor’s quasispecies is diverse.

Transmissible compartment: the viral subpopulation in the donor tissue / fluid that is actually sampled for transmission (e.g., nasopharyngeal vs gut; within‑host compartmentalization affects what subset is passed on).
