#  Objecive
Developed a Neural network model to predict gas pipelines' (primary) failure time  based on input parameters like  pipe material, pipe diameter, fitting material, type of  pipe joint and  coupling type, using historical data. (Using data Filed as per CFR codes,  USA)  
# Cleaning the data
Initially, many columns are present in the dataset with a large number of duplicate entries. So the required input features need to be selected, and the required data needs to be extracted from the given data set. Initially, we started with a large number of columns but ended up with only seven features and 12,000 observations of data (rows) after the cleaning.
# Feature Selection
Since a large number of features are available initially, not all the features correlate with the service. So we need to figure out what all features correlate with service time. First, data were standardized, and formatting was normalized, then all NULL and duplicate values were removed.
For feature selection, box and whisker plot of service time vs. pipe diameter was analysed.
Despite a positive trend as expected, a decrease was observed beyond a central maximum. 
Increasing frequency of pipe material as plastic was hypothesized as the probable cause and further confirmed.
Strong dependance on material used (Categorical variable) was thus observed.
Material of pipes, fitting were hence selected for the model.
Further, altitude values were analysed and were rejected on accounts of low/ no correlation.
Variations upon fixing diameter values as well as material were still observed.
These were attributed to joint types and the involved coupling and hence they were included in the analysis as well.
#  Implementation
After trying out various geometries, we arrived at a possible arrangement where the NN had 5 input layers (4 for categorical inputs and 1 for numerical input), 4 embedding layers (for 4 categorical inputs), a concatenation layer, 5 dense layers, with selective L2 weight decay in some (with 5 intermittent batch normalizations and 2 dropout layers in between). The data size was large and consisted of both categorical variables and numerical values. To tackle this situation, we took help of embedding layer and batch normalization. Embedding layer - for translating high-dimensional vectors into low-dimensional spaces. In order to inculcate the categorical variables (encoded with ordinal encoding) as a sparse input.Batch normalization - for faster training and to make the behaviour of the gradient stable.
# Results & Conclusions
With successive trial and error runs, we were able to obtain a model with satisfactory outputs by varying model (Hyper-)parameters including the model structure, regularizing options, gradient descent learning rate etc.
Our model was able to give decent predictions with the mean square error (Validation) coming out to be nearly 30 to 35 for 30 epochs.
These results support our hypothesis that machine learning can use pipe diameter, pipe material, fitting material, type of pipe joints and coupling type to predict gas pipeline leakage time with considerable accuracy. 
It was worth noting that owing to the intermittent regularization, the output obtained showed a lower Validation MSE than Training MSE.
