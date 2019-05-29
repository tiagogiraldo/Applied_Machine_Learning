# Applied_Machine_Learning-Computer_Vision-PlantVillage_Disease_Classification_Challenge
Transfer Learning applied to PlantVillage Disease Classification Challenge Crowd ai


In this notebooks are applied transfer learning applied to a PlantVillage Disease Classification Challenge hosted by [crowdai](https://www.crowdai.org/challenges/plantvillage-disease-classification-challenge), more especifically it was a resnet 50  network  applied.  But the data is highly unbalanced, for that reason I try some approach modifying the number of images in training set and dev set, and changing some network parameters.

The challenge is ended, for that reason the forecast was evaluated with the same sample and used the accuracy as metric.

In sample challenge, the classes has this composite.


| Statistic | Images By Label |
|:---       |             ---:|
|count      |        38.000000|
|mean       |       576.763158|
|std        |       505.201027|
|min        |        64.000000|
|25%        |       299.500000|
|50%        |       436.500000|
|75%        |       695.500000|
|max        |      2321.000000|

I try first [oversampling](https://towardsdatascience.com/handling-imbalanced-datasets-in-deep-learning-f48407a0e758), it is copying the files by a rule, it is, copying the files in the same class as number of times of files are contained in the maximum number of a class (2321/64 in the minimum class). The network is too slow and doesn't converged, few days running the network and the accuracy stayed in 10% in average.

Then, I [oversampled](https://towardsdatascience.com/handling-imbalanced-datasets-in-deep-learning-f48407a0e758), in this case, I sampled to every class the minimum quantity of files conteined in a label (64). The result was much better, the training set accuracy was 99% and for dev set was 81%, really much better than whole data set and oversampled data set.

Later, I worked with mean (576) , first (300) and third (695) quartil, and a arbitrary number of 1500 files.  In this trials, when the class o label has a lesser number of files that threshold selected, I didn't sampled under the threshold, and instead, I'd take all files in the class, and I'd only sampled when the class has a higher number of files than threshold. The results was better in all case, with similar values in accuracy metric.
