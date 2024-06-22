# Marketing Optimizer for Blue Field Agency
## Objective
This Marketing Optimizer is designed for Blue Field Agency in the form of an interactive Jupyter Notebook to optimize marketing campaign spendings using MMM with Linear regression method, Logistic regression method and Random Forest Algorithm. Marketeer can choose between two KPIs to optimize: 
1. number of engaged sessions generated,
2. conversion.

## Model
The repository contains the following files:

### marketing_opt_report.ipynb:  
The interactive Jupyter Notebook functions as the user interface reading the file **auto_report_read_file.py**. It automatically generates various graphs and visualizations to assist marketers in comprehending the effectiveness of 3 different marketing campaigns. Emphasis was placed on reducing user input. In order to use the optimizer, end-users are required to input specific parameters due to the requirement: specify KPI to optimize, the minimal budget attribution each campaign and total budget, provide the pathname to the dataset, and determine date of Dutch sports event and Dutch holiday and major music festival event. 

### auto_report_read_file.py:      
The Python script that contains the core functions and algorithms that execute the MMM analysis and data visualization. Core functions include:
- **data_reader** (read the provided pathname and exlude the data before first peak),
- **set_dummy_for_date** (sets specific date into dummy variables 1),
- **build_model_ols_rf** (builds the OLS and random forest regressor if KPI = 'engagedSessions_reset',
                         at the same time apply RandomizedSearchCV for hyperparameter fine tuning, and provide budget allocation advice at the end),
- **build_model_lr_rf** (builds logistic regression and random forest classifier if KPI='conversions_reset'
                         at the same time apply RandomizedSearchCV for hyperparameter fine tuning, and provide budget allocation advice at the end),
- **marketing_optimizer** (links together the above-mentioned functions; takes user-defined parameters as an input).
This Python script contains a detailed documentation describing each function.

## Prerequisites

### Installation:
Required libraries for this model are provided in the text file **libraries_list.txt**
To install required packages, the following code will be used:
```
pip install library_name
```
you can replace "library_name" with the needed library.


## User input
The table below summarizes the user input required by **marketing_opt_report.ipynb**.

| Parameter | Data type | Description |
| :---:     | :---:     | :---:       |
| pathname | String	| Pathname to the dataset containing historical data |
| target_date_sports | String	| Specifies the date has important Dutch sports event in 'YYYY-MM-DD' format |
| target_date_festival | String	| Specifies the date has Dutch holiday and/or a major music festival in 'YYYY-MM-DD' format |
| KPI |	String	| Choice of KPI that is optimized: number of Engaeged sessions (engagedSessions_reset) or conversions (conversions_reset) |
| budget	| Float	| Monetary value that is assigned to today’s marketing allocation mix |
| min_ShoppingReset	| Float	| Minimum budget allocation for campaign ShoppingReset |
| min_ResetSearch	| Float	| Minimum budget allocation for campaign ResetSearch |
| min_ResetAfterDrinkSearch	| Float	| Minimum budget allocation for campaign ResetAfterDrinkSearch |
