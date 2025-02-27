# SASOM: Score-Based Association Tests for Somatic Mutations and Multinomial Outcomes

[![License](https://img.shields.io/badge/license-LGPL--2.0-blue.svg)](https://www.gnu.org/licenses/old-licenses/lgpl-2.0.html)

## Overview


Cancer is a highly heterogeneous disease with distinct subtypes, making it essential to understand their association with genetic variations for targeted therapy development. Somatic mutations play a crucial role in tumor progression, but their low prevalence poses a challenge for statistical analysis.  We propose **Subtype Analysis with Somatic Mutations (SASOM)**, a method for analyzing the association between cancer subtypes and sets of somatic mutations, incorporating functional mutation data. Simulation studies confirm that SASOM maintains correct type I error and outperforms alternative methods in detecting associations. Applying SASOM to a cutaneous melanoma dataset, we identify a genetic pathway linked to immune-related subtypes, demonstrating its potential for cancer research.

The SASOM has been implemented into the SASOM package. The **SASOM** package implements score-based association tests to assess the relationship between somatic mutations and multinomial outcomes, such as disease subtypes. The package is particularly suited for genomic studies and supports a flexible framework for combining p-values using different statistical methods.

### Features:
- **Score-based association tests** for somatic mutations and multinomial outcomes.
- Flexible p-value combination methods: `DAPC`, Fisher's, and Tippet's methods.
- Accommodates both **fixed** and **random** genetic variant effects.

## Installation
You can install the tcrl package by downloading the SASOM_0.1.0.tar.gz file to your local system. Once downloaded, install it from your local file path using the following command in R:

```{r}
install.packages("path/to/SASOM_0.1.0.tar.gz", repos = NULL, type = "source")
```
## Usage

```{r}
# Load the package
library(SASOM)

str(SASOM.data)
 List of 4
  $ y: int [1:500, 1:3] 0 0 0 0 0 0 0 0 0 0 ...
  $ X: num [1:500, 1:3] 1 1 1 1 1 1 1 1 1 1 ...
   ..- attr(*, "dimnames")=List of 2
   .. ..$ : NULL
   .. ..$ : chr [1:3] "X0" "X1" "X2"
  $ G: int [1:500, 1:20] 0 0 0 0 0 0 0 0 0 0 ...
  $ W: num [1:2, 1:20] 1 1 1 1 1 1 1 0 1 1 ...
   ..- attr(*, "dimnames")=List of 2
   .. ..$ : chr [1:2] "W0" "W1"
   .. ..$ : NULL
```

`SASOM.data` is a synthetic dataset designed to illustrate the usage of the **SASOM** function, which evaluates associations between somatic mutations and multinomial outcomes, such as cancer subtypes. The dataset includes simulated genetic, covariate, and outcome data for 500 subjects.  

The dataset is structured as a **list containing four key components**. The **`y` matrix** represents multinomial outcomes, where each row corresponds to a subject and each column to a subtype, with values summing to 1 to indicate exclusive subtype membership across three categories. The **`X` matrix** contains covariates, including an intercept term, capturing clinical or demographic information for each subject. The **`G` matrix** holds genetic variant data, indicating the presence or absence of somatic mutations across 20 variants for each subject. Additionally, the **`W` matrix** provides variant annotations, linking genetic variants to relevant genomic features such as genes or pathways.  

This dataset serves as a demonstration tool for applying **SASOM** to test the association between **somatic mutations and multinomial outcomes**, offering a structured framework for evaluating the genetic basis of disease subtypes.

```{r}

# Load the example dataset
data(SASOM.data)

# Run the SASOM test with all p-value combination methods
result <- SASOM(SASOM.data$y, SASOM.data$X, SASOM.data$G, SASOM.data$W, p.comb = "all")

# View the results
print(result)
pval.theta     pval.tau     p.fisher     p.tippet       p.dapc
4.810743e-05 6.840567e-05 6.756756e-08 9.621254e-05 6.958715e-08
```

The **SASOM** function performs a score-based association test to evaluate the relationship between **somatic mutations** and **multinomial outcomes**, such as disease subtypes. It assesses both **fixed effects**, which assume a consistent variant effect across all subjects, and **random effects**, which allow the effect to vary between individuals. The function provides multiple **p-value combination methods**, ensuring robust hypothesis testing in genomic research, particularly when analyzing **multiple outcomes influenced by covariates and genomic features**.  

The results from running SASOM on `SASOM.data` indicate statistical significance across multiple combination methods. The **fixed effect p-value (`pval.theta`)** is **4.81e-05**, while the **random effect p-value (`pval.tau`)** is **6.84e-05**, both suggesting a notable association between somatic mutations and disease subtypes. The overall p-values, derived using different combination methods, further reinforce this conclusion. **Fisher’s method (`p.fisher = 6.76e-08`)** and the **Data-Adaptive P-value Combination (DAPC) method (`p.dapc = 6.96e-08`)** yield the most significant results, while **Tippet’s method (`p.tippet = 9.62e-05`)** provides a more conservative estimate.  

These findings suggest a strong association between somatic mutations and multinomial outcomes. By incorporating multiple statistical approaches, SASOM provides a versatile and powerful framework for hypothesis testing in cancer research and other genetic association studies.
## Citation

If you use **SASOM** in your research, please cite the following:

Liu, M., Liu, Y., Wu, M.C., Hsu, L. and He, Q., 2021. *A method for subtype analysis with somatic mutations*. Bioinformatics, 37(1), pp.50-56.

## Authors

- Meiling Liu ([mliu@fredhutch.org](mailto:mliu@fredhutch.org))
