# Bias in Data
### Agustin Lew
### 10/17/2019

## Goal

The goal of this assignment is to explore the concept of bias through data on Wikipedia articles on political figures from a variety of countries. 

## Data sources used
To create these tables, we will draw from two data sources:

Page_data.csv: It lists Wikipedia politician articles by country. It can be found at https://figshare.com/articles/Untitled_Item/5513449. 

It contains three columns: 

•	‘page’: title of the Wikipedia article.

•	‘country’: country of the politician in the article.

•	‘rev_id’: revision ids for the articles. Will be fed into the ORES API.

WPDS_2018_data.csv: It lists countries and regions, and their populations. The dataset is drawn from the world population datasheet published by the Population Reference Bureau.

It contains two columns:

•	‘Geography’: country or region. 

•	‘Population mid-2018 (millions)’: The population for that country or region. For region, it is calculated by doing an aggregate sum of the countries corresponding to that region.

## Resources used

This analysis was prepared using Python 3.7.3 running in a Jupyter Notebook environment.

Documentation for Python can be found here: https://docs.python.org/3.5/

Documentation for Jupyter Notebook can be found here: http://jupyter-notebook.readthedocs.io/en/latest/

The following Python packages were used, and their documentation can be found at the accompanying links:

Pandas 0.24.2: https://pandas.pydata.org/pandas-docs/version/0.24.2/

Requests 2.21.0: https://pypi.org/project/requests/2.21.0/

In addition, the ORES REST API is used to obtain the predicted category for the articles. The documentation can be found at https://ores.wikimedia.org/v3/#!/scoring/get_v3_scores_context_revid_model, while an example can be seen in the jupyter notebook of this assignment, located in the src folder. The ORES API requires the revision ids for the articles (‘rev_id’) in order to return a prediction.

## Files Created

This notebook creates seven CSV files of data extracted and compiled as part of this analysis.

The first file is wp_wpds_contries-no-match.csv, which contains the articles for which the country or region was not found in the wpds_2018_data.csv dataset. Contains columns ‘page’, ‘country’, and ‘rev_id’.

The second file is wp_wpds_api_call_errors.csv, which contains the articles for which the ORES API returned an error when fed its revision code. Contains columns ‘article_name’, ‘country’, ‘revision_id’ and ‘population’.

The third file is wp_wpds_politicians_by_country.csv, which contains the merged dataset by combining page_data.csv and WPDS_2018_data.csv. Contains columns: ‘country’, ‘article_name’, ‘revision_id’, ‘article_quality’, and ‘population’. ‘article_quality’ was obtained from the ORES API.

The fourth file is wp_by_country.csv, which contains information for each country. The columns are ‘country’, ‘num_article’, ‘population’, ‘coverage’, ‘B’, ‘C’, ‘FA’, ‘GA’, ‘Start’, ‘Stub’, ‘high_quality’, and ‘region’.

The fifth file is wp_by_region.csv, which contains information for each region. The columns are ‘region’, ‘num_article’, ‘population’, ‘coverage’, ‘B’, ‘C’, ‘FA’, ‘GA’, ‘Start’, ‘Stub’, ‘high_quality’,

The columns in the last two csv files mean:

•	‘country’/’region’: The country or region the row pertains to.

•	‘num_article’: the number of articles for that country or region.

•	‘population’: the population for that country or region.

•	‘coverage’: number of politician articles as a proportion of country population. (percentage)

•	‘high_quality’: relative proportion of politician articles that are of GA and FA-quality. (percentage)

•	‘B’, ‘C’, ‘FA’, ‘GA’, ‘Start’, ‘Stub’: the number of articles that were predicted to be in that category.

The sixth file is high_quality_by_region.png, which is an image showing a bar plot for percentage of high-quality articles by region.

The seventh file is coverage_by_region.png, which is an image showing a bar plot for coverage percentage by region.
## Visualizations Created

The tables and bar plots can be seen in the results section of the jupyter notebook file ‘hcde-a2-bias-in-data.ipynb’. The bar plots are also saved in the results folder as a .png file.

## License

This assignment code is released under an MIT License.

The Wikipedia page_data.csv dataset is licensed under the CC-BY-SA 4.0 license.

The WPDS_2018_data.csv dataset is copyrighted by the Population Reference Bureau.
