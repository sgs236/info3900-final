## Summary

The project investigates the relationship between maternal incarceration and high school graduation status using data from Wave 4 of the ADD Health longitudinal study.

### Installation and Run Guide

1. Download this repository
2. Navigate to the repository directory
3. Uncomment the following lines in your code and run them to install the required libraries:

```
install.packages('tidyverse')
install.packages('dplyr')
```

### Adding Columns to Dataset

1. Find corresponding columns in the dataset

See **additional notes**

2. Add columns to select call

```
select(H4WP3, H4WP4, H4WP5, H4WP24, H4OD4, H4EC1, H4EC7, H4LM28, H4ED7, H4EO7, BIO_SEX4, H4ED1)
```

3. Filter the column

```
filter(H4WP3 <= 1) %>% # Filter out refused or don't know for H4WP3
  filter(H4ED1 <= 4) %>% # Filter our don't know for H4ED1
  mutate(H4WP4 = case_when(H4WP4 >= 97 ~ NA, .default = H4WP4),
         H4WP5 = case_when(H4WP5 >= 94 ~ NA, .default = H4WP5),
         H4WP24 = case_when(H4WP24 == 7 ~ NA, .default = H4WP24),
         H4EC1 = case_when(H4EC1 >= 96 ~ NA, .default = H4EC1),
         H4ED7 = case_when(H4ED7 >= 5 ~ NA, .default = H4ED7),
         H4EC7 = case_when(H4EC7 >= 96 ~ NA, .default = H4EC7),
         H4EO7 = case_when(H4EO7 > 4 ~ NA, .default = H4EO7))
```

### Additional Notes

Visit the ADD Health Codebook Explorer for detailed variable descriptions.

https://addhealth.cpc.unc.edu/documentation/codebook-explorer/
