# T-shirt-Size-Classification
Simple classification using K-nearest neighbor (KNN) algorithm.

![image-4](https://github.com/radiadus/T-shirt-Size-Classification/assets/55176713/3e539b4f-067a-41f3-b3d4-1673d7b46e03)

In this project I’m using K-Nearest Neighbor algorithm to predict T-shirt size based on height and weight of various people. This simple project was an assignment for my Machine Learning course back in the 3rd semester. First we have a dataset of height, weight, and T-shirt size as in image below.

![t-shirtsize](https://github.com/radiadus/T-shirt-Size-Classification/assets/55176713/434a37cd-703d-4cd4-a2b3-5b37852f6035)

_(18 data of height, width, and T-shirt size)_

Then we assign height and weight as our features and T-shirt size as our target. After that we will use MinMaxScaler() from sklearn.preprocessing as our scaler for our features. MinMaxScaler will preprocess the data and turn it into range in between 0 until 1. Here is the result of our features after we preprocessing it using MinMaxScaler

    from sklearn.preprocessing import MinMaxScaler

    scaler = MinMaxScaler().fit(features)
    features = scaler.transform(features)
    print(features)
    print(target)

![image5](https://github.com/radiadus/T-shirt-Size-Classification/assets/55176713/4c8cc434-bc76-403f-9fe3-00c7bccc942c)

_(left is height and right is weight)_

Lets plot our data first so we can see them clearly.

![image-6](https://github.com/radiadus/T-shirt-Size-Classification/assets/55176713/cb01a88e-ab2d-44fa-82d7-0a0642e1ebd8)

_(blue is medium size and black is large size)_

After that I used KNeighborsClassifier from sklearn.neighbors and set n_neighbors=5 also metric=’euclidean’. This means our KNN model will use Euclidean distance as their metrics to calculate the distance of new data with every data we had before. N_neighbors=5 means that we will look for 5 nearest data and see which group is dominant. 

    from sklearn.neighbors import KNeighborsClassifier
    
    knn = KNeighborsClassifier(n_neighbors=5, metric='euclidean')
    knn.fit(features, target['Ukuran Kaos'])

For our test data we have a data that has 161 cm height and 61 KG weight. Then we do prediction for the T-shirt size and we got the result which is ‘M’ means it’s probably medium size.

![image-7](https://github.com/radiadus/T-shirt-Size-Classification/assets/55176713/09d311af-6bc9-4fad-9cf5-053034dd9769)

_(Our prediction code and the result for testing data)_

And here is the plotting for our new data. 

![image-8](https://github.com/radiadus/T-shirt-Size-Classification/assets/55176713/1cfe5946-05e1-4603-9a30-ac0776a96e00)

_(red dot is the testing data)_

From the plotting we could see that the new data or testing data is closer to four blue dots which it is medium size. Then we could conclude that the testing data is probably using medium T-shirt size.
