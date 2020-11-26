# Seattle Airbnb EDA
In the attached notebook I explore data gathered by Inside Airbnb (http://insideairbnb.com/get-the-data.html) and hosted on Kaggle (https://www.kaggle.com/airbnb/seattle/data) to investigate whether investors and non-investors are meaningfully separable groups in the context of occupancy rates. This analysis follows CRISP-DM methodology, as outlined in the following steps:

Business understanding: Should individuals let property management companies handle their Airbnb listings for a cut?

Data understanding: 1 dataset with characteristics of listings, 1 availability calendar. Should be able to (i) find investor hosts and (ii) calculate occupancy rates.

Data preparation: Please see attached Jupyter Notebook.

Modeling/Evaluation: We use an independent t-test to gauge whether mean occupancy rates between investor and non-investor groups have a statistically significant difference between them.

Accompanying description/article: https://alexsiebelmckenna.medium.com/are-airbnb-management-companies-really-worth-it-f21ac730c4c5
