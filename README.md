## Impact Analytics CV Assignment

**Instructions on how to run the project**

Clone the repository and setup the project with dependencies mentioned in [Requirements.txt](https://github.com/surabhisohoney/ia-cv-assignment/blob/master/requirements.txt).  
Run `python Cifar_10_exp1.py`   
Run `python Cifar_10_exp3.py`

Alternatively, shared Google Colab notebooks of all the experimentations can also be used to run and check the results right away.


**Network Details**

The network is defined using references of previously used networks of which details are as below:
- In first and second experiments [**Cifar_10_exp1.py**], the network uses 5 CNN layers followed by 2 fully connected layers.   
- In experiment 3 [**Cifar_10_exp3.py**], two more CNN layers were added.

More number of CNN layers are used to create deeper network which can learn complex fetaures in an image. Also it would not be beneficial to increase number of layers above some extent because output feature dimention gets reduced after convolution at each stage. As input is 32*32, using a huge deep netwok will not make any significance, which is the reason behind using 5 CNN layers. 

On Cifar10 dataset, some small and local features can differentiate objects better than global features. Smaller size filters can capture local features very well. So, **3*3** filter is used.  
It has been seen that increasing number of filters in progressive layers lead to learning deeper features resulting in better accuracy.

**Hyperparameter Details**  

- Tried experimenting with different batch sizes, i.e. 128 and 256. Batch size 128 gave better results. Further experiments with different batch sizes can be done. Larger batchsize was chosen instead of something like 32 or 64, due to large dataset and faster training requirement.

- Typical values chosen for learning rates are 0.01, 0.001, 0.0001. It is observed in literature that training converges smoothly with LR = 0.01 on Cifar10 dataset, which led to choosing 0.01 for LR.

**Optimizer**: 
Stochastic Gradient Descent (SGD) is used as an optimiser. Gradient discent is an optiomization algorithm used in majority of ML tasks and it is used for updating weights of the Neural Network(NN) in each iteration. SGD is a type of gradient descent in which a few samples are selected randomly instead of the whole data set for each iteration, making it faster and computationally less expensive. Other optimization algorithms can also be used in place of SGD, e.g. AdaM, AdaGrad

**Loss Function**: 
Categorical Cross Entropy is used as a loss function which is usually used in case of single label classification problems, i.e. when each data point belongs to one perticular class. This gives us the probability distribution of samples on the classes. 

**Accuracy Matrices**: 
Confusion matrix is used as an accuracy measure which gives summary of the prediction results on the given classification problem. The number of correct and incorrect predictions are summarized with count values and broken down by classes. Other than this F1 score can also be used as an accuracy measure.

**Challenges Faced**
- Validation accuracy was higher than training accuracy in first attempt. Adjusted Learning Rate and Decay Factor to rectify.

**Results**  

Without Batch Normalization, accuracy achieved is 82.22% [[accuracy_exp1.png](https://github.com/surabhisohoney/ia-cv-assignment/blob/master/accuracy_exp1.png)]  
With Batch Normalization, accuracy achieved is 83.85% [[accuracy_exp2.png](https://github.com/surabhisohoney/ia-cv-assignment/blob/master/accuracy_exp2.png)]

In experiment 3, two types of augmentations were done.  
1. Horizontal Flip 
2. Rotation by 15 degrees 

Accuracy achieved with this is 85.35% [[accuracy_exp3.png](https://github.com/surabhisohoney/ia-cv-assignment/blob/master/accuracy_exp3.png)]  
> Given plot for experiment 3 is only for last 80 epochs indicating that loss is not saturated and can be reduced further by more training

**Future Enhancement**
- Used network can also be modified and fine-tuned by adjusting number layers, filters and by fine-tuning hyperparameters.
- Problem can be addressed by using ResNet architectures which will result in better accuracy.
- Transfer learning can also be implemented to achieve better accuracy.
- Other type of data augmentations can also be tried, i.e. Shifting, Scaling, etc.
