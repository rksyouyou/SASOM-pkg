# SASOM: Score-Based Association Tests for Somatic Mutations and Multinomial Outcomes

[![License](https://img.shields.io/badge/license-LGPL--2.0-blue.svg)](https://www.gnu.org/licenses/old-licenses/lgpl-2.0.html)

## Overview

**SASOM** is an R package that implements score-based association tests to assess the relationship between somatic mutations and multinomial outcomes, such as disease subtypes. The package is particularly suited for genomic studies and supports a flexible framework for combining p-values using different statistical methods.

### Features:
- **Score-based association tests** for somatic mutations and multinomial outcomes.
- Flexible p-value combination methods: `DAPC`, Fisher's, and Tippet's methods.
- Accommodates both **fixed** and **random** genetic variant effects.

## Installation

You can install the development version of SASOM from GitHub using the following commands:


```{r}
# Install devtools if necessary
install.packages("devtools")

# Install SASOM from GitHub
devtools::install_github("yourusername/SASOM")
```
## Usage

```{r}
# Load the package
library(SASOM)

# Load the example dataset
data(SASOM.data)

# Run the SASOM test with all p-value combination methods
result <- SASOM(SASOM.data$y, SASOM.data$X, SASOM.data$G, SASOM.data$W, p.comb = "all")

# View the results
print(result)

```

## Citation

If you use **SASOM** in your research, please cite the following:

Liu, M., Liu, Y., Wu, M.C., Hsu, L. and He, Q., 2021. *A method for subtype analysis with somatic mutations*. Bioinformatics, 37(1), pp.50-56.

## Authors

- Meiling Liu ([mliu@fredhutch.org](mailto:mliu@fredhutch.org))
