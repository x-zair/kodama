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
- 

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
