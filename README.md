# Project 1 - Machine Learning: Exploring Nonlinearity for the Landlord-Tenant Problem

## Research Question

What is the relationship between a tenant’s price of energy and their lease structure (whether they are responsible for paying for energy) on their energy consumption?

## Data

To analyze the relationship between price, lease structure, and energy consumption, I use data from the 2015 Residential Energy Consumption Survey (RECS). The dataset is published publicly by the U.S. Energy Information Administration. It includes a representative sample of over 5,000 residences throughout the United States, and it includes 763 descriptors for each residence from their total energy use to the Energy Star status of each major appliance. Together, the 763 data points on each residence detail the residence’s energy set-up and consumption for one year.

Unfortunately, the subset of data I am able to analyze is much smaller. Only a subset of the 2015 RECS dataset is about tenants, with the rest being homeowners. Furthermore, the dataset includes many imputed data points, flagged accordingly. Taking only observations corresponding to tenants with all essential data present, my analysis is left with a sample size of 569 residences. Of these, 134 have their natural gas included in rent, while 435 pay for their own natural gas. Appendix A shows the percentage of residences located in each of the nation’s 10 census
divisions for the data I use in my analysis and for the RECS data as a whole. Please find the appendix in my full report at landlord-tenant.pdf. Certain regions such as the East North Central are significantly more represented in the used subset than in the full RECS dataset, while others such as the South Atlantic. These differences likely reflect the differences in the prevalence of rentals between regions. Appendices B and C display the dataset’s summary statistics and plot the dataset, respectively. 

## Methodology:

I explore two relationships in my analysis. The first is the relationship between the actual price of natural gas and the amount of natural gas used. The second is the relationship between the effective price of natural gas from the tenant’s perspective and the amount used. The only difference between these metrics, is that for a tenant whose natural gas is included in their lease, the effective price of natural gas is zero.

I estimate each relationship employing two methods. First, I use OLS to regress the quantity of natural gas used on the price of natural gas (either effective or actual), including a linear, a squared, and a cubed term. I control for household income. More control variables would make the analysis more robust, but due to the small sample size they could cause overfitting. Second, I estimate the relationship between the quantity of natural gas and the price of natural gas using a multilayer perceptron. Again, I control for household income.

## Results:

Appendix D tabulates the results of my OLS regressions. Appendix E plots each regression’s curve of best fit against the scatterplot of data. Please find the appendix in my full report at landlord-tenant.pdf.

Unsurprisingly, for the actual price regression, I received a negative linear coefficient, suggesting that as prices increase natural gas consumption decreases. Notably, there was also a positive quadratic coefficient, suggesting that as prices continue to increase the marginal reduction in consumption decreases. This result likely reflects decreasing marginal utility for each unit of energy used; while tenants are likely to heat their homes to a certain livable level regardless of the price, additional heating for comfort is likely to be more price elastic.

Interestingly, in the effective price regression we do not see the same clear decline in demand. In fact, the linear coefficient is positive, suggesting that consumption increases as does price. That said, the regression’s curve of best fit in Appendix E is generally quite flat. This difference could be reflective of a positive correlation between a landlord paying for utilities and a residence’s energy efficiency.

Appendix F reports on the R2 scores of the multilayer perceptron. Appendix G plots the models’ curves of best fit against the scatterplot of data.

After many training experiments with different learning rates, activation functions, numbers of hidden layers, hidden layer sizes, my multilayer perceptrons were unable to pick up on trends beyond the mean. As seen in Appendix F, both perceptions have very near-zero R 2 scores, suggesting that they were unable to represent a significant pattern beyond the mean of the training data.

Please see landlord-tenant.pdf for analysis and conclusions.

## Replication Instructions

In order to replacate my results, download the Jupyter notebook and dataset from this repository. Adjust the reletive filepath of the dataset in the notebook to its location on your machine, and run the notebook. Consult recs_data_codebook.xlsx for the meaning of the columns in the dataset.
