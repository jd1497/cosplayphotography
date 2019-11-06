# Costume Art and Photography- Project
I will help direct costume artists to increase popularity in the pictures that they take by enhancing
their costume pictures. To do this, I will test how different color payouts (the percentage of each color in
individual pictures, ranging from white, black, red, blue, yellow, green, purple, and cyan) and different
proportions of one color (from the largest proportion to the smallest proportion) affect the popularity of
that specific picture in WorldCosplay, a site consisting of artists and photographers that do costume play,
for this project. I wanted to use this model to benefit costume artists to enhance their production, and if
this model is proven that higher number of likes comes from a higher percentage of certain colors, this
should mean that costume artists should focus more on photography and photo editing tools such as
photoshop to produce better pictures and increase the amount of popularity they will gain catering their
productions to catch and draw more audiences. I extracted the data of all the colors from the images, since
the data does not exist, using the PHP tool Image Color Extract to extract image data on the percentage of
each color one by one, and put them into an csv file to run an analysis with R.

As a part of data curation, I currently have 1000 sample data from the WorldCosplay website.
The data will not be repeated. The percentages, which are the units in decimal points, are between 0 and
1, which is consistent. The number of likes and the persons, which details the number of people, as well
as the proportions of colors are all extracted from the images themselves. Ambiguous data does not exist
for my data set, as it concerns the analysis of color in the data, except that the huge proportions of either
white or black classified in the dataset might be due to the contrasts of the other colors (red, blue, yellow,
green, cyan, and purple) mixed with either one of those colors (white or black) that had the system show a
high percentage of white or black when classifying pictures. Because the units provided are consistent, I
don’t need to scale and center the data, but I have came up with binary data such as classify as 0 if the
number of likes does not exceed the mean number of likes of the overall data with the outliers (which is
40), and classify as 1 otherwise, for SVM analysis purposes. My codes will run for all the data points
regardless to see which model and which method will be best to calculate the amount of popularity a
picture will receive with certain colors. I also converted my findings for each data point into a whole new
dataset, which are the different proportions of one color arranged from the largest proportion to the
smallest proportion from the data that I have collected, in which Color1 represents the largest proportion
of one color and Color8 represents the smallest proportion of a different color that exists in one picture.
In addition, I will also determine whether there are other factors other than color that influences
the number of likes, or the popularity, of the photographic costume work, such as the number of people
displayed in the picture. Its application would provide more research and allow increase in the quality of
photographic work for artists who enjoy costume play but also wanted to look for rooms to improve on
their work in the future. The customers would be artists and photographers in costume play who are
looking to improve on the arts of their trade.

The number of likes is discrete, which is a dependent variable, and the independent variables
(percentage of blacks, white, red, blue, yellow, purple, green, and cyan) are continuous. There was no
data at all for this project, and I would have to gather each data by myself in the WorldCosplay website
by downloading a random sample of 1000 pictures (without repetition), and then clean each data point
one by one by submitting them into the Image Color Extract PHP (www.coolphptools.com/color_extract)
with reduced gradient, reduced brightness, 8 colors, and a delta of 255. Therefore, there are missing data,
but not redundant data. As for the overall data set, I am dropping outliers, such as the ones that contain
more than a certain number of likes (100) due to popularity of the costumer, which affects the statistical
data. This might, in turn, result in a better analysis on the number of likes a person can garner in the
website due to the quality and the colors of the picture, not the number of fans you already have.

The analysis techniques, especially the numerical estimation techniques that I’ve selected include
polynomial regression, principle component analysis, the best subset, linear regression models,
bootstrapping, bagging, decision trees, random forests, and neural network, since this returns the number
of likes a person can gain from either using the different proportions of one color or the proportions of
different colors as the determinant features. As for the classification technique, because this is not a
classification problem, using quadratic discriminant analysis (QDA) and the LDA are not suitable, nor
will using logistic regression or the KNN classifier work, because I wanted to find how many likes certain
portions of colors generate. I find that the SVM might not be possible to determine the number of likes
one receives in a picture for this project, but I managed to create a binary dataset, by classifying the
pictures that does not exceed the average number of likes overall as 0 and the rest as 1 to run a support
vector machine analysis and see how contrast (the percentage of blacks and the percentage of whites)
factor into the popularity of that picture. Hence, these techniques are sub-optimal, and should not be
included. The conclusion I could draw from my SVM model is that only with a very high cost would the
predictors show that anything above 40 likes can be obtained, which correlates with the website trend that
obtaining anything beyond 30 or 40 likes is difficult for the linear kernel. Same with the radial kernel,
where when the gamma is very high, the predictors that show anything above 40 can be obtained at
random areas in the plot, which is not effective in classifying a specific area that predicts the trend of
pictures above 40 likes as the linear kernel does, but it also showed that obtaining 40 likes is difficult.

For exploratory analysis to visualize the data and determine the best techniques, I mainly use the
PCA analysis. As you can see in the graph below, the proportion of variance explained by each factor are
effective up to 6 to 8 principle components, as each principle component analysis explains almost the
same proportions of variance, which shows that the factors matter up to 6 to 9 components for the
percentage of different color data set. I chose to select 6 features to run my other regression models and
compare that to when I run all, as it explained above 80% of the overall data. As for the proportions of
one color data set, most of the variance explained by each factor are effective up to 4 to 6 principle
components, in which I select 4 features (the lowest that explain above 80% of my overall data) in my
other regression models for comparison.

For my results, I used a series of methods ranging from neural networks, decision trees, random
forests, generalized linear model, and linear regression models, but the best model for the percentages of
different colors would be a neural network with 2 different hidden layers with 8 nodes in the first hidden
layer and 5 nodes in the second hidden layer to get one output, which is the number of likes. The input
parameters, or the features, are the different colors (percentages of black, white, red, blue, yellow, green,
purple, and cyan), and the output layer would be the number of likes. The best result for the
proportions of one color ranging from the largest to the smallest would be a neural network with 2
different hidden layers with 5 nodes in the first and second hidden layers to get one output, which is the
number of likes. The input parameters, or the features, are the proportions of one color ranging from
the largest to the smallest (from Color1 to Color8). The reason why other methods do not work is
that random forests, generalized addictive model, local regression, linear regression, lasso, ridge
regression, bootstrapping, bagging, and decision trees have high MSE and high test error rates, as
you can see in the Appendix. The lowest error rate would be the neural network, in which I
would repeatedly run and train the neural network at least 10 times and filter out the number of
hidden nodes that have a higher MSE compared to the others, and usually training and test errors
are close to the same. In terms of stable results and stable training and test errors without tedious
training the data, random forests and decision trees would be better, as it gives the second lowest
MSE next to the neural networks.

The generalized addictive model, smoothing splines, regression splines, and local
regressions might need more time to tune the data before getting a lower MSE than decision trees
and bootstrapping, and generally, they are harder to tune and therefore ended up with a high
MSE than linear regression models. Forward, backward, and best subset selections does not work
in terms of testing their CP, adjusted R-squared, and the BIC model to only contain either 1 or 2
variables as important in predicting the number of likes one can garner from a picture, and in
addition to having a high MSE, due to some pictures that does not have that specific factor that
determine the fluctuation of likes as when the Percentage Purple, the Percentage Blue, Color 5,
and Color 4 are determined to be important, that specific picture would have to rely on the
intercept coefficient to determine the amount of likes that they are going to garner, which shows
to be inaccurate.

Feature selection, Cross-validation results, ROC curve, additional models, and best
models (at the end of every appendix) are shown below. For future improvements, I believe that
gathering data to analyze different levels of popularity (the ones over 40 likes and 150 likes) in
addition to features that might have a direct effect on how the picture became popular would be
helpful to improve this model, such as following the person, looking at the ratio of the number of
followers versus the number of people that the person follows, and for classification results and
purposes, whether that specific costume falls under certain genres. Overall, my model turned out
well with neural nets, and I will continue to improve on this model further for the times to come.
