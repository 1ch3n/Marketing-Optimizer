# Marketing Optimizer for Blue Field Agency
Marketing Optimizer for the use of Blue Field Agency was prepared in the form of an interactive Jupyter Notebook designed to optimize marketing spendings using MMM with Linear regression method, Logistic regression method and Random Forest model. Marketeer can choose between two KPIs to optimize: 
1. number of engaged sessions generated,
2. conversion.

The repository contains the following files:

### marketing_opt_report.ipynb:    
The interactive Jupyter Notebook that works as the user interface reading **auto_report_read_file.py**. The system generates a series of graphs and visualizations to aid marketeers in understanding the performance of different marketing campaigns. Minimizing the user input was prioritized. Besides running the non-modifiable cells, the end-user needs to adjust the user-defined parameters: specify KPI to optimize, the minimal budget attribution and total budget constraints, provide the pathname to the dataset, and determine the binary values for dummy variables (Dutch sports event and Dutch holiday and major music festival event). 


### auto_report_read_file.py:      
The Python script that contains the core functions and algorithms that execute the MMM analysis and data visualization. Core functions include:
- **build_model_elastic_net** (applies data transformation to capture adstock and saturation effects, builds the Elastic Net regression model),
- **hyperparameter_optimizer** (applies the Nevergrad algorithm that searches for the set of hyperparameters that minimizes model's MAPE),
- **eval_charts** (creates data visualization based on the predicted KPIs: the most efficient budget allocation mix by ROI, contribution and funnel chart),
- **perform_optimization** (defines bounds and contraints of the optimization problem; returns an interactive bar chart with budget allocation recommendation),
- **marketing_optimizer** (links together the above-mentioned functions; takes user-defined parameters as an input).

This Python script contains a detailed documentation describing each function.

## Prerequisites
Text file **libraries list** contains required libraries. Most of the libraries used are not installed on the system by default. Hence, they need to be installed beforehand.

### Installing:
This can be done by copy-pasting this cell:
```
pip install library_name
```
and replacing library_name with the corresponding name of the library.

On the example of *sklearn* library, copy-paste this cell:
```
pip install scikit-learn
```

## User input
The table below summarizes the user input required by **marketing_opt_report.ipynb**.

| Parameter | Data type | Description |
| :---:     | :---:     | :---:       |
| KPI to optimize |	String	| Choice of KPI that is optimized: number of sessions (sessions_reset) or total revenue (totalRevenue_reset) |
| Minimal attribution |	Float |	Percentage of the total budget that needs to be allocated to each of the RESET campaigns |
| Total allocation budget	| Float	| Monetary value that is assigned to today’s marketing allocation mix |
| Pathname to dataset	| String	| Pathname to the dataset containing historical data |
|All-important Dutch  sports event (dummy)	| Binary	| Specifies whether today is an important Dutch sports event or not |
|Dutch holiday and biggest music festivals (dummy)	| Binary	| Specifies whether today is Dutch holiday and/or a major music festival |
