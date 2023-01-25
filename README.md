Filtering structural variants in a long read human trio dataset
----------------------------------------

# Overview

# Getting our data

Reference:

VCF:

PED file:

# Initial assessment

Let's look at our VCF and get a basic understanding of it.

- How many variants are there in this VCF?
```


```

- What kind of variants are present in this file? Does it contain all SV types?

```



```


- How does this file look different from the VCF we looked at in the small variant / file formats section?

```




```


- What chromosome(s) do these variants come from? 

```

```


# Filtering our data

Let's filter our data to find **Mendelian Violations**. A Mendelian Violation (or "Mendelian Inheritance Error", MIE)
is when a child contains a genotype that is not present in either of its parents. How could this variant have appeared if it
wasn't inherited?

```



```

To locate Mendelian Violations, we can use the GATK SelectVariants tool.
We need to use a [PED file](https://gatk.broadinstitute.org/hc/en-us/articles/360035531972-PED-Pedigree-format), which describes the relationship between samples in a family.

Which sample corresponds to the child? The mother? The father?

```


```

The GATK command to detect Mendelian Violations is below:

```bash
# From: https://www.biostars.org/p/279427/

gatk \
 SelectVariants \
 --mendelian-violation True \
 -ped family.ped  \
 --output putative_mies.vcf \
 --variant GIAB_Trio.sample.vcf
```

This should produce a file called `putative_mies.vcf`. How many variants are in this file? What genotypes do they have?

```


```

# Looking for common variants?

