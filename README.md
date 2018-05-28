# DrivingScene

- We introduce a large-scale dataset
with over 110k images, dubbed DrivingScene, covering traffic
scenarios under different weather conditions, road structures,
environmental instances and driving places.
- We propose a multi-label neural network, which incorporates both single- and
multi-class classification modes into a multi-level cost function for
training with imbalanced categories. This architecture is further
enhanced by a deep data integration strategy to improve the
classification ability on hard samples.

# Scene Corpus
we provide 52 different kinds of driving scenes, cutting across common driving instances,
weather conditions, places and road structures. The scene category word-tree is shown.
![zhanwj](https://github.com/zhanwj/DrivingScene/blob/master/work-tree.PNG)

# Deep data integration
Two categories about processing biased data: re-sampling, which aims to balance the class priors by under-sampling the majority classes or over-sampling the minority classes, and cost-sensitive learning, which assigns higher misclassification costs to the minority
classes than to the majority ones. In order to combined both categories
into CNN approaches, we design a multi-label architecture, which incorporate both single- and multi-class training
 by a multi-level loss function. Can be seen as followed.
![zhanwj](https://github.com/zhanwj/DrivingScene/blob/master/architecture.PNG)
One question left unsolved, which is how to effectively conduct sampling for selected single-labels for each single-labels side. A sample method is that small classes can be chosen during the training procedure, however, as the weight values are fixed, it is more likely to make the network overfitting on small tag groups. So we adapt the AdaBoost algorithm in an additional data layer to manage the sampling process, keeping the classification balanced between multiple label tags. We also estimate the attention area  for our four super classes in each single-labels side. For an image sample to be classified, the label belonging to the weather category is assigned to the top area of the image. The road structure class and the road instance class are usually found in the bottom area of images. And the place class is mostly related to the central image area.

# Result
52 categories are sorted into three groups: small tag group with sample number less than 1000, medium tag group with a sample number between 1000 and 10000, and big tag group  with more than 10000 samples.
The Baseline1 resamples the foreground and background image
patches for learning a convolutional neural network, the Baseline2
encodes super classes by the knowledge from a confusion
matrix, which proposes a multi-scale architecture with
two CNNs. The shallow CNN is used to extract features of the
super classes and aims to integrate minority class information
into the deeper CNN.

Following those strategies, we show PR-curves as followed,which shows that our method achieves a much higher precision
in terms of the same recall value compared with other baselines.
![zhanwj](https://github.com/zhanwj/DrivingScene/blob/master/PR-curves.PNG)
# Visualization of the Deep Features
We first utilize the test set of DrvingScene (i.e., 55k images) as the input for the network. Then we sort all the images
according to the activation responses of neural units in one layer. Finally we take the top 100 deconvolution images with
the largest responses as the receptive field (RF) visualization of the units at the layer of Pool5.
![zhanwj](https://github.com/zhanwj/DrivingScene/blob/master/Visualization.PNG)
