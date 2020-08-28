# CS660 HW 3
## Group Member
- Yan Li
- Smith Amornsaensuk
- Chengyi Wang

## Spam Classifier using PySpark
### Usage
Run 
```
Spam Classifier PySpark.ipynb 
```
in Jupyter Notebook or Google Colab to see the results.

### Results
Laplace smoothing Value | Accuracy | Precision | Recall | Run Time |
----------------------- | -------- | --------- | ------ | -------- |
0   | 0.9052173913043479 | 0.9423076923076923 | 0.3161290322580645| 0:00:01.300303 |
0.25| 0.9686956521739131 | 0.8287292817679558 | 0.967741935483871 |0:00:01.130442|
0.5 | 0.971304347826087  | 0.8426966292134831 | 0.967741935483871 |0:00:01.052726 |
0.75| 0.9730434782608696 | 0.8563218390804598 | 0.9612903225806452|0:00:01.095822 |
1   | 0.9756521739130435 | 0.8713450292397661 | 0.9612903225806452|0:00:01.055738 |
2   | 0.9791304347826087 | 0.9171974522292994 | 0.9290322580645162|0:00:01.047157 |

### Conclusion
We can see that without smoothing factor i.e. smotting = 0 the model does a bad job on recall. 
The reason that model yeild high accuracy with smooth = 0 is that the unblance of classes in the data set i.e. the class prior is 0.87 and 0.13. As we increase the 
laplace smoothing value, the accuracy is also increase. However the recall does not change a lot with the laplace smoothing value from 0.25 to 1. But as you can see
the run time did not change a lot.

## Spam Classifier using MapReduce
### Preprocessing

### Training

### Classify

### Evaluation
