# Analysis of Swimming Dataset using R

## Introduction
Swimming is one of the most popular and competitive sports in the world, encompassing a diverse range of strokes. The Olympics feature four major strokes:

- **Freestyle**
- **Backstroke**
- **Breaststroke**
- **Butterfly**

Each stroke requires unique techniques, strengths, and strategies, making it interesting to explore the performance dynamics of swimmers who specialize in different strokes versus those who participate across multiple strokes.

In competitive swimming, flexibility can give athletes an advantage by improving their adaptability, strength, and endurance. However, specializing in one type can provide distinct benefits, such as mastering specific techniques. This study examines the question:

### **Do swimmers who compete in different types of swimming earn more medals?**

## Objective
The goal of this analysis is to uncover patterns and relationships that highlight the role flexibility plays in swimming success. By analyzing the Paris Olympics 2024 Swimming Dataset, we aim to determine whether participation in multiple swimming styles correlates with a higher likelihood of earning medals.

## Dataset
The dataset, sourced from https://www.kaggle.com/datasets/piterfm/paris-2024-olympic-summer-games , contains detailed information about swimmers, their participation in different swimming events, and their performance measures at the Paris 2024 Olympics. The dataset includes fields such as:

- **Athlete Name**
- **Country**
- **Age**
- **Gender**
- **Event Type** (e.g., freestyle, backstroke)
- **Medals Won** (gold, silver, bronze)
- **Participation Across Events**
- **Performance Metrics** (e.g., times, rankings)


The chosen dataset (Paris Olympics 2024 Swimming Results) is robust, but contains a large number of columns with redundant or missing values. This requires cleaning and refining.

For this project, the key columns that are relevant to our analysis are: `participant_name`, `participant_code`, `event_code`, and `rank`.

We make several modifications to the dataset to fit the needs of our research question.

## Data Wrangling
The given dataframe is manipulated to capture the number of unique swimming types participated in by each swimmer. This facilitates a more focused analysis of multi-style participation.

### Filtering:
- Rows with missing values in the `rank` column are removed, as these do not contribute to the analysis.
- Rows where the `participant_type` is "Team" are excluded, as team-based events are not relevant to our hypothesis. We focus on individual swimmers.
- Rows where the `event_type` is a medley event are removed, as medley events involve all four swimming styles and could dilute the specificity of the analysis.
- Columns with redundant data are excluded. Several columns in the dataset (for example `discipline` and `event_code`) contain the same value through all rows in the dataset.
- Columns with data not in focus of this project are excluded (e.g., `gender`, `venue`, `date`, etc.).

## Data Transformation
A number of derived columns are created for aiding in the analysis as follows:

- **`swimming_type`**: Extracted from the `event_name` column to identify the specific swimming stroke for each event.
- **`medal_type`**: Derived from the `rank` column to categorize the performance into medal tiers (e.g., Gold, Silver, Bronze).
- **`event_weightage`**: Represents the importance of the result based on the `event_stage` column. Each stage is assigned a weightage based on whether the result is from a Heat event, Semifinals, or Finals. This will be useful to visualize data by scaling up more important results.
- **`standardised_performance`**: A normalized column with values ranging from 0 to 1, calculated from the `rank` column. A value of 1 indicates the best performance, and 0 indicates the worst.
- **`n.types`**: A new column capturing the number of unique swimming strokes a swimmer has participated in. In this dataset, this value is between 1 and 4.

With these adjustments and transformations in place, the dataset becomes well-structured and aligned with the requirements of our analysis. These steps ensure that the data is ready for exploring the relationship between participation in multiple swimming types and performance outcomes.

## Methodology
The analysis is conducted using **R**, leveraging libraries and techniques suitable for data wrangling, visualization, and statistical modeling. Key steps include:

1. **Data Preprocessing**
   - Cleaning and formatting the data.
   - Handling missing values and outliers.
2. **Exploratory Data Analysis (EDA)**
   - Summarizing key statistics.
   - Visualizing participation patterns and medal distributions.
3. **Statistical Analysis**
   - Comparing medal counts between swimmers specializing in one stroke versus multiple strokes.
   - Identifying significant trends in performance metrics.
4. **Visualization**
   - Plotting trends to illustrate the impact of flexibility versus specialization.

## Tools and Libraries
This project utilizes the following R libraries:

- `tidyverse` (for data manipulation and visualization)
- `ggplot2` (for creating advanced plots)
- `dplyr` (for data wrangling)
- `readr` (for reading datasets)
- `stats` (for statistical analysis)

## Results
The analysis results aim to:

- Highlight whether swimmers participating in multiple strokes earn more medals than those specializing in one.
- Provide insights into the trade-offs between flexibility and specialization.

## How to Run the Analysis
1. Clone this repository:
   ```bash
   git clone https://github.com/SumayyaAli11/Analysis-of-Swimming-dataset-using-R.git
   ```

2. Set up the required R environment. Install necessary libraries by running:
   ```R
   install.packages(c("tidyverse", "ggplot2", "dplyr", "readr"))
   ```

3. Open the R Project.Rmd and run the analysis scripts in the R console or RStudio.

## Acknowledgments
- **Dataset**: Sourced from https://www.kaggle.com/datasets/piterfm/paris-2024-olympic-summer-games .
- **Olympics**: Data pertains to the Paris Summer Olympics 2024.

## License
This project is licensed under the MIT License. See the `LICENSE` file for details.

---
Thank you for exploring this repository! Feel free to contribute by suggesting improvements or reporting issues.
