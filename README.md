# ml_KNeighbours

Data set (Sales-Win-Loss data set) used contains the sales campaign data of an automotive parts wholesale supplier.  

It was available from IBM Watson website, but cannot find it anymore so I included it in this repo.


I explored the data by printing the shape, first 5 entries and columns. There are 19 columns and 78025 entries. 
The columns are 'Opportunity Number', 'Supplies Subgroup', 'Supplies Group', 'Region', 'Route To Market', 'Elapsed Days In Sales Stage', 'Opportunity Result', 'Sales Stage Change Count', 'Total Days Identified Through Closing', 'Total Days Identified Through Qualified', 'Opportunity Amount USD', 'Client Size By Revenue', 'Client Size By Employee Count', 'Revenue From Client Past Two Years', 'Competitor Type', 'Ratio Days Identified To Total Days', 'Ratio Days Validated To Total Days', 'Ratio Days Qualified To Total Days', 'Deal Size Category',

The target chosen is opportunity result – either won or loss. I dropped the opportunity number which is an index and tried running the data with 3 different models – Guassian Naïve Bayes, Linear Support Vector Classification and K Nearest Neighbours. The KNN model performed the best at 0.817 accuracy. The linear SVC did not converge. I changed the number of nearest neighbours to 5 instead of the default 3 to get a better result. I printed out the confusion matrix for the 3 different models to get a better sense of the results. Next I printed out the correlation matrix to check which columns I should drop. 

Using the matrix as a guide, I drop the 'Total Days Identified Through Closing', 'Opportunity Amount USD', 'Supplies Subgroup', 'Competitor Type', 'Client Size By Employee Count', 'Client Size By Revenue columns. I run the KNN model again with the reduced features, and this time the accuracy reaches 0.847. I print out the classification report which states the f1 scores as the opportunity results is heavily skewed towards losses and f1 may be a better metric when there is a imbalanced class distribution as in this case. The f1 scores for both won and loss have increased from 0.545 to 0.618 and 0.886 to 0.904 respectively.
I check the results with a confusion matrix, and now I remember that I should use the stratified shuffle split to maintain the class ratio after splitting. The original split actually did not alter the ratio much, but I try the stratified shuffle split to see whether the results can be improved.
The accuracy improves marginally from 0.847 to 0.849. It classified 1 more won correctly, and 53 more losses correctly.
