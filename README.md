# CS660 HW 3
## Group Member
- Yan Li
- Smith Amornsaensuk
- Chengyi Wang

## Spam Classifier using PySpark
### Usage
Open 
```
PySpark.ipynb 
```
in Jupyter Notebook or Google Colab and run all the cells to see the results.

### Results
Laplace smoothing Value | Accuracy | Precision | Recall |F-measure| Run Time |
----------------------- | -------- | --------- | ------ | ------- | -------- |
0   | 0.9052173913043479 | 0.9423076923076923 | 0.3161290322580645| 0.47342995169082125 | 0:00:01.300303 |
0.25| 0.9686956521739131 | 0.8287292817679558 | 0.967741935483871 |0.8928571428571429 |0:00:01.130442|
0.5 | 0.971304347826087  | 0.8426966292134831 | 0.967741935483871 |0.9009009009009008|0:00:01.052726 |
0.75| 0.9730434782608696 | 0.8563218390804598 | 0.9612903225806452|0.905775075987842 |0:00:01.095822 |
1   | 0.9756521739130435 | 0.8713450292397661 | 0.9612903225806452|0.9141104294478527 |0:00:01.055738 |
2   | 0.9791304347826087 | 0.9171974522292994 | 0.9290322580645162|0.9230769230769231 |0:00:01.047157 |

### Conclusion
We can see that without smoothing factor i.e. smotting = 0 the model does a bad job on recall. 
The reason that model yeild high accuracy with smooth = 0 is that the unblance of classes in the data set i.e. the class prior is 0.87 and 0.13. As we increase the 
laplace smoothing value, the accuracy is also increase. However the recall does not change a lot with the laplace smoothing value from 0.25 to 1. But as you can see
the run time did not change a lot.

## Spam Classifier using MapReduce
### Preprocessing
Run the following code to separate the spam data into two files named train.txt and test.txt under Data folder.
```
python3 preprocess.py
```
### Training
Run the following code to get the training data which we can use in the classify step. The script will save the probability from training data in model.json file
```
!python train_mrjob.py ./data/train.txt > model.json
```
The script will save the probability from training data in model.json file

### Classify
Run the following code to get the predicted label for the test data.

Note: By changing the parameter **--laplace** to see how the laplace smoothing value affect the accuracy.
```
!python classify_mrjob.py data/test.txt --model=model.json --laplace=0.1 > prediction.txt
```
### Evaluation
Run the following code to see the results.
```
python3 evaluation.py
```
### Results
Laplace smoothing Value | Accuracy | Precision | Recall |F-measure| 
----------------------- | -------- | --------- | ------ | ------- | 
0.1  | 0.9856 | 0.9216 | 0.9724| 0.9463
0.25| 0.9820 | 0.8981 | 0.9724 |0.9338 
0.5 | 0.9749  | 0.8545 | 0.9724 |0.9097
0.75| 0.9677 | 0.8150 | 0.9724|0.8868 
1   | 0.9668 | 0.8068 | 0.9793|0.8847 

## Conclusion
