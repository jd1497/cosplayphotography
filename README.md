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
