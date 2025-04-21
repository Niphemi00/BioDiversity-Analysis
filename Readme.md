# README: Analysis of Species Protection and Observations in National Parks

## Overview
This project performs a comprehensive analysis of two datasets:
1. `species_info.csv` - Contains data about species, including category, scientific and common names, and conservation status.
2. `observations.csv` - Contains the number of observations of species in different national parks.

The goal is to understand patterns in species protection across categories and parks and to explore potential relationships between protection status and observation frequency.

---

## Step-by-Step Breakdown

### Step 1: Importing and Inspecting the Data
- Loaded `species_info.csv` and `observations.csv` using Pandas.
- Examined the structure, column names, and data types.
- Identified missing values and null records.

### Step 2: Checking for Null Values
- Used `isnull().sum()` to check for missing data.
- Ensured data completeness by confirming that there were no critical nulls in the columns required for analysis.

### Step 3: Creating `is_protected` Column
- Created a new column `is_protected` in `species_info` to indicate whether a species is under protection.
```python
species_info['is_protected'] = species_info['conservation_status'] != 'No Intervention'
```

### Step 4: Chi-Squared Test
- Created a contingency table for species category vs protection status.
- Performed a chi-squared test to assess the independence of species category and protection.
- The resulting p-value was 0.45, indicating **no significant association** between category and protection status.

### Step 5: Visualizing Protection Status
- Bar chart: Percentage of protected observations by park.
- Pie chart: Percent of protected species by category.
```python
plt.bar(percent_protected_obs['park_name'], percent_protected_obs['percent_protected_observations'])
```

### Step 6: Filter to Threatened or Endangered Species
- Filtered the species to only those marked as "Threatened" or "Endangered".
- Calculated the percentage of observations that are protected.

### Step 7: Visualizing Total Observations by Category
- Grouped data by species category and summed observations.
```python
total_observation_by_category = special_and_observations.groupby('category')['observations'].sum()
```
- Visualized with a bar chart.

### Step 8: Pie Chart of Protected Percent by Category
- Created a pie chart showing how protection is distributed across different species categories.
```python
protection_df['percent_protected'].plot(kind='pie', autopct='%1.1f%%')
```

### Step 9: Relationship Between Observations and Protection
- Merged protection data with total observations.
- Created a scatter plot to examine if categories with more observations are more protected.

---

## Conclusion
- Most categories have a small percentage of protected species.
- No significant statistical relationship between category and protection status.
- Visualization helps to clearly distinguish patterns across parks and categories.

---

## Tools Used
- **Python** (pandas, matplotlib, seaborn)
- **Statistical analysis** (Chi-squared test)

---


