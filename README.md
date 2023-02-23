Overview(what should be done in first 2 steps)
Business and Data Understanding
    Explain your stakeholder audience here
Modeling
Regression Results
Conclusion

# Real Estate Analysis

## Business Understanding

King of the Deck, a deck design company, has requested that we conduct research for them. They are considering expanding their business to indoor renovations as well. They want to know given a certain amount of space to renovate if it's a better investment to create an outdoor deck or indoor living space. We are tasked with creating a model that predicts house prices, and within that model seeing the affect of each extra square foot of deck space vs living space on overall house price.

<div>
<img src="Images/houses.jpg", width = 600, height = 300/>
</div>

Photo by <a href="https://unsplash.com/photos/f9qZuKoZYoY">Avi Waxman</a> on <a href="/@grstocks">Unsplash</a>

## Data Understanding
 
Most of our data was pulled from <a href="https://info.kingcounty.gov/assessor/DataDownload/default.aspx">King County Assessor Data Download</a> 

import pandas as pd 
import seaborn as sns
import matplotlib.pyplot as plt
%matplotlib inline
import statsmodels.api as sm
import numpy as np
import scipy.stats as stats
from sklearn.metrics import mean_absolute_error
from sklearn.preprocessing import StandardScaler

We begin by loading and then previewing our data

#we will call our data "re" which stands for real estate
url = 'https://raw.githubusercontent.com/learn-co-curriculum/dsc-phase-2-project-v2-5/main/data/kc_house_data.csv'
df = pd.read_csv(url)
re = df.copy()
re.head()


Our data is different numeric and categorical statistics or describers of houses. Each row in the data represents one house. Our target factor(aka y variable) in the data set is price. For all the other columns we will be looking to see it's affect on price. Many of the columns describe square footage of different areas in a house. Others describe when it was built, quality, address, and various other descriptive statistics.


With a brief scan of some of the addresses it seems that all of the houses are in the United States. However, let's right a short code to confirm this

re['address'].str[-14:].value_counts()



