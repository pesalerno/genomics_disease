# genomics_disease

===

There are three genomics and disease datasets used in this study. 

- Colorado mountan lions distributed in the western slope and Front Range, 12444 SNPs, 134 individuals and 0.881594 genotyping rate. **DISEASE DATA INFO HERE** 

- California mountain lions in the LA Basin Area, 9651 SNPs, 88 individuals and 0.729214 genotyping rate. **DISEASE DATA INFO HERE** 

- California bobcats in the LA Basin Area, 13649 SNPs, 281 individuals and 0.843702 genotyping rate. **DISEASE DATA INFO HERE** 




#

#

1.Do individual inbreeding coefficients predict apathogenic disease presence? 
---


1. **Get filtered SNP matrices**

Link this to the puma project for how to get the matrix outputs. 

2. **Filter for Linkage Disequilibrium in all three datasets** 

I filtered for LD using plink with the following code: 

	plink --noweb --file mydata --r2 --out outputfilename 
	
	
The CO puma dataset only had 23 loci pairs with r2>0.5, the CA bobcat dataset had zero loci pairs with r2>0.5, and the CA puma dataset had xxx loci that had r2>0.5. 

In order to create a blacklist of loci in LD to exclude form the SNP matrix, we used find/replace arguments in TextWrangler to create a list of SNPs like this:

	59185_31
	539339_84
	52224_62
	49662_45
	348531_41
	##       ...etc

And then using this file (named **LD-loci-list.txt**) we generate our LE SNP matrix using *plink*: 

	./plink --file filename --exclude LD-loci-list.txt --recode --out LD-filtered


The resulting CO pumas matrix had 12427 SNPs remaining, and the resulting CA pumas matrix had 9367 SNPs. 

3. **Obtain F_h measure in *plink* for all three datasets**

We estimated the Fh heterozygosity measure which is a proxy for individual inbreeding using the code: 

	plink --noweb --file mydata --het --out outputfilename


4. **Run LMMs and other basic stats for all datasets together**


5. **Run LMMs for each dataset separately** 


#

#


2.Do individual SNPs predict apathogenic disease presence? 
---

1. Run GWAS analyses in plink with unfiltered LD datasets for all three datasets.

To perform a standard case/control study, we performed a simple asosciation study in plink: 

		plink --file filename --assoc #add --ci 0.95 for a 95% CI estimation

Which gives you chisquare odds ratio test results for each allele. Then, we performed a standard case/control study using Fisher's Exact test (allelic association) to generate significance: 

	plink --file myData --fisher 

2. Run GWAS analyses in another program... 



3. BLAST all loci that came out as correlated, even ones in LD. Of the loci that come out as correlated to the trait, find out which of those are in LD and list BLAST results by LD group. 


 


