# data-analysis-projects
### Author: Ayşegül Ada Benhür

Two small statistical studies that use country-level data to answer questions about development and society. Each project includes a Jupyter notebook with the full analysis and a PDF report that summarises it.

### Project	Question	/ Method	/ Data year

* 1.2 – Population:	Is having a large population beneficial for a country?	/ Linear regression (OLS) /	2015
* 1.3 – Education & Democracy:	Does a higher level of education lead to a more democratic society? /	Multivariate logistic regression /	2020


## 1.2 – Is having a large population beneficial for a country?

  ### Predictions
  * Countries with larger populations tend to have lower life expectancy.
  * Countries with larger populations tend to have lower GDP per capita.
    
  ### Approach
  Kept 2015 data only, which gives 119 countries.
  Log-transformed population and GDP per capita (base 10) because both are strongly skewed.
  Fitted two simple linear regressions with log10(Population) as the predictor.
  
  ### Results
  Model	/ Coefficient on log10(Population)	/ p-value /	R²
  
  * Life expectancy ~ log10(Population)	/ −2.22	/ 0.018	/ 0.047
  * log10(GDP per capita) ~ log10(Population)	/ −0.184	/ 0.002 /	0.077

  Both relationships are statistically significant and support the predictions. The low R² values show that population size explains only a small part of the differences between countries.

  
## 1.3 – Does a higher level of education lead to a more democratic society?

  ### Causal assumptions (DAG)
  GDP per capita → Schooling → Democracy, and GDP per capita → Democracy. GDP per capita is treated as a confounder, so the model controls for it.
  
  ### Predictions
  * More years of schooling lead to a higher chance of being a democracy.
  * Higher GDP per capita is associated with a higher chance of being a democracy.
  
  ### Approach
  Merged three datasets on country and year and kept 2020, which gives 136 countries.
  Turned the political regime score (0–3) into a binary variable: 0–1 = autocracy, 2–3 = democracy.
  Fitted a logistic regression: Democracy ~ log10(GDP per capita) + Schooling.
  Showed the coefficients and their 95% confidence intervals in a forest plot.
  
  ### Results (Pseudo R² = 0.169, LLR p < 0.001)
  
  Predictor	/ Coefficient / p-value /	95% CI
  * Schooling (years)	/ 0.406 /	0.002 /	[0.145, 0.667]
  * log10(GDP per capita), standardised	/ 0.049 /	0.881	/ [−0.599, 0.698]
  
  The first prediction is supported. The second is not, once schooling is controlled for.
  

## How to run
pip install pandas numpy seaborn matplotlib statsmodels networkx scipy jupyter
jupyter notebook
Open a notebook from inside its project folder so that the CSV files load correctly.

## Tools

Python · pandas · NumPy · seaborn · Matplotlib · statsmodels · NetworkX
