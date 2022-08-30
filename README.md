# AI_Working_With_Sparse_Data_Example
 Introducing a personal idea about "Information Gain to specific class recognition" working with very "sparse" and "unbalanced" dataset about genes. Learning project in Vinbigdata
 
 This project works with very "sparse" dataset about genes. There are only 115 samples on training dataset but I have about 1.2 million field for these samples. Every 2 fields next to each other forms a pair of genes. In each field, 0 is missing value, 1 is weak single gene, 2 is strong single gene. Value pairs that often appear are 0.0 ie null, 1.1 ie set of 2 weak genes, 1,2 ie set of 1 weak gene 1 strong gene and 2,2 means 2 strong genes. 
 
 Because the data is too many fields and large, opening the dataset through pandas read_csv is not suitable for personal devices. So through pairing 2 fields side by side to reduce the number of fields by half, and at the same time collect all the data on the list and add back to the dataframe is the method used to open and read this dataset.
 
 There are 2 classes for output, PCT and Control, in which both train and valid dataset are very unbalanced and lean towards Control. However, the important task here is to find a way to classify the PCT.
 
 The methods developed as well as the evaluation will be used to develop the ability to recognize PCT.
 
 Construction method ideas include:
1. Use normal machine learning techniques
2. Use information gain and collect the highest IG fields 
3. Use K-means to cluster the fields then select the cluster that can best classify PCT
4. Use information gain for only PCT and collect the fields with the highest IG values of this type.

Formula for idea 4 about Information Gain for only PCT:

![equation](https://latex.codecogs.com/svg.image?IG_{PCT}&space;=&space;E_{const}&space;-&space;\sum_{i}^{K}\frac{No.(i_{PCT})}{No.(PCT)}*\log_{2}&space;\frac{No.(i_{PCT})}{No.(i)})

Where i is type i of sample in field with K types.

The result is f1-score in valid set, for first 3 ideas, result is 0, for last idea, f1-score is 0.4
This result is quite high (even the highest result in my class with the idea of harvesting features using 2 times evaluates feauture important only 0.13 while my idea about IG for only PCT reaches 0.4 with just collecting 5 features with IG value).
However, because this is a dataset with too few samples, this result does not completely evaluate the true ability of this idea (idea can fit with this data set, but not sure to generalize correctly).

Furthermore, 0.4 is actually a low result, so this idea is for reference only and the incorporation of other feature collection ideas with this idea will be done in the future.

