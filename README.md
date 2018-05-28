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

# Method
Two categories about processing biased data: re-sampling, which aims to balance the class priors by under-sampling the majority classes or over-sampling the minority classes, and cost-sensitive learning, which assigns higher misclassification costs to the minority
classes than to the majority ones. In order to combined both categories
into CNN approaches, we design a multi-label architecture, which incorporate both single- and multi-class training
 by a multi-level loss function. Can be seen as followed.
![zhanwj](https://github.com/zhanwj/DrivingScene/blob/master/architecture.PNG)
One question left unsolved, which is how to effectively conduct sampling for selected single-labels. We adapt the AdaBoost algorithm in an additional data layer to manage the sampling process, keeping the classification balanced between multiple label tags. As misclassified samples are with higher probability to be chosen, the network is more generalized in recognition of various traffic scenes. We also estimate the attention area per class for our four super classes in each single-labels side. For an image sample to be classified, the label belonging to the weather category is assigned to the top area of the image. The road structure class and the road instance class are usually found in the bottom area of images. And the place class is mostly related to the central image area. If more than one category appears in same image, the minority class will be prioritized.

