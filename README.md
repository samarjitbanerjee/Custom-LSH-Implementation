# Custom-LSH-Implementation

This is a Custom Implementation of LSH method in KNN.Text Review along with labels has been used in this approach.
Steps followed to implement the same.

1) Perform Spliting Train and Test Data on the Review Data. Test Data Labels are NAN. Train Labels are 'tech', 'business', 'sport', 'entertainment', 'politics'.
2) Implement TFIDFVectorizer on the Train Data(Perform fit_Transform operation on Train Data) and  make use of both bigrams & trigrams and also limit the max features to 4000 and minimum document frequency to 10
3) Create Random 5 hyperplanes where values of the vector has to be taken from Standard Normal Distribution.
4) Implement custom Hashfunction to calculate the dot product between transformed TFIDFVector of Train Data and each Weight Vector, if the value(scaler)[Dot product of (1*4000).(4000*1)]
is < 0 mark the value as '-1', else '+1' and create a hashtable where the key should be the values obtained from dot product and value should be the index of the Datapoint and Data Array
5) Use the above implemented hashfunction in the Test Data after performing only TFIDFVectorizer Transform operation on Test Data and based on the hastable key value obtained 
from the dot product of test data and weight vector, we will determine the nearest points.
6) Calculate cosine-sim between test data points and nearest points and sort the data in descending order as cosine-sim value should lie between -1 and 1(Range of cos(x) lies
between -1 to +1).As the angle between two vectors tend to 0, they can be treated as nearest poins. Cosine distance for those vectors will tend to zero.
[cosine-distance = 1- cosine-sim]
7) Find 11 nearest neighbours for test data points and perform Majority Vote.In case of a tie in the obtained labels from nearest neighbours, you can pick a label after 
sorting all the labels alphabetically(A-Z), i.e. for example labels starting with A would get more preference than labels starting with Z.
8) We have used Grader function to validate the accuracy.
