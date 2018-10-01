## Logistic Regression

X and y are all put in columns

in NN, it will be easier to separate $\theta$ and bias $b$ instead of combine them as a big theta ($b=\theta_0$)

Rafidah's effect: if y = 1 we try to make y-hat large and if Y = 0 we try to make y-hat small.

Loss func: for single sample
Cost func: on entire training set; avg.

use log format as it is a convex func so we can find the global minimum.

logistic regression can use 0 initialization.


derivative == slope


chain rule

we usually use dv to preresent d_final_output/d_v, meanning the final output by the special variable v.

dJ/du = dJ/dv * dv/du
dJ/db = dJ/dv * dv/du * du/db
these derivative terms are all corresponding to lines(weight) link neurons.

So by forwarding we can get output from input, by BP we can get derivatives.


in deep learning period, vectorization definitely can speed up.


## Vectorization

both CPU and GPU can process SIMD (single instruction multiple data) when using built-in func. without distinct for loop, but GPU is marked as much better

use reshape to make sure the matrix is the dimension u want.
broadcasting in python: copy the second matrix to make element wise operation possible.


not use rank 1 array in np (shape = (5,)), instead use randn(5,1) instad of randn(5)
assert(a.shape == (5,1)) to make sure.
if get a rank 1 array, use reshape to make it as a matrix.



regression cost function:

$log(\hat{y}^y(1-\hat{y})^{(1-y)}) =ylog(\hat{y})+(1-y)log(1-\hat{y})$


 add a minus to make minimize the loss func. = maximize the prob.


### Cost function
In mathematical optimization, the loss function, a function to be minimized.
In artificial neural networks, the cost function is a function that the network wants to minimize

The loss function quantifies the amount by which the prediction deviates from the actual values


minimize the cost J = do the ML when the dataset is IID(identical distribution) on samples.



QUIZ and CODE tips:

 1. we generally say that the output of a neuron is a = g(Wx + b) where g is the activation function (sigmoid, tanh, ReLU, ...).


2. One common preprocessing step in machine learning is to center and standardize your dataset, meaning that you substract the mean of the whole numpy array from each example, and then divide each example by the standard deviation of the whole numpy array. But for picture datasets, it is simpler and more convenient and works almost as well to just divide every row of the dataset by 255 (the maximum value of a pixel channel).


Common steps for pre-processing a new dataset are:
- Figure out the dimensions and shapes of the problem (m_train, m_test, num_px, ...)
- Reshape the datasets such that each example is now a vector of size (num_px \* num_px \* 3, 1)
- "Standardize" the data




learning rate:
- Different learning rates give different costs and thus different predictions results.
- If the learning rate is too large (0.01), the cost may oscillate up and down. It may even diverge (though in this example, using 0.01 still eventually ends up at a good value for the cost). 
- A lower cost doesn't mean a better model. You have to check if there is possibly overfitting. It happens when the training accuracy is a lot higher than the test accuracy.
- In deep learning, we usually recommend that you: 
    - Choose the learning rate that better minimizes the cost function.
    - If your model overfits, use other techniques to reduce overfitting. (We'll talk about this in later videos.) 
