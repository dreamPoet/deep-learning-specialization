## setting up

1. train/dev/test sets

previous: 60/20/20 good for 100-10000

now: for big data, dev big enough for evaluation is ok,

1,000,000 -> dev and test sets are 10,000 separately is OK, so 98/1/1

make dev/test come from same distribution if your training set are different distribution.

unbiased model needed: then test set is necessary.

deal with high bias first then high variance.


## regularization

L2 regularization(also called weight decay as it equals to times original w with a scaler smaller than 1):
$\frac{\lambda}{2m} ||w||^2$

L1 regularization:
$\frac{\lambda}{(2)m} |w|$

Frobenias norm:
$||w^{[l]}||_F^2 = \sum^{n^{[l-1]}}_{i=1}\sum^{n^{[l]}}_{j=1}(w^{[l]}_{ij})^2$

F norm of matrix has similar form with L2 but was not call as L2.


weight decay: A regularization technique (such as L2 regularization) that results in gradient descent shrinking the weights on every iteration.


**there can be 2 or no 2, it's just a scaling factor**

L1 will lead to sparse w.

lambda is a key word in py, so do not use it directly.

in the original regression model, we add 1 to X to make $\thetaX$ where $\theta_0 = b$, so in regularization we sum from $\theta_1$ to $\theta_n$. here we just sum all $w$ and discard $b$

lambda increase, penalize much, so W is smaller, so corresponding features are less influence to the final output. so the NN is simpler (if some w = 0, the it can be a smaller NN). on the other hand, w is smaller, then z is smaller, then a tanh neuron can be seen as linear -> the whole NN can be seen as linear.

choose different keep-prob for diff layer, for layers much more likely to happen overfitting, use lower keep-prob.


drop-out is commonly used in CV area as data is always not enough so overfitting always happened. 

The disadv is it makes cost does not so distinct, so cannot use graph to debug. so in debugging, close drop-out.


data augmentation: flap; distortion; cutting; 


disadv of early stopping: orthogonalization: considering one task in one time; early stopping combine two tasks. use L2 regularization to replace early stopping but need to try lost of lambda.

## optimization


1. normalization
- substruct mean
- divided by variance


training and test set should use same mean and variance.

---


Xavier Initialization: initialize the weights of the network so that the neuron activation functions are not starting out in saturated or dead regions. we want to initialize the weights with random values that are not “too small” and not “too large.”

gaussian * np.sqrt(2/n), has variance 2/n

---
grad check:

to avoid vector too large or too small, divided by the sum of their length (to make comparision easier)



CODE TIPS:

**What you should remember**:
- The weights $W^{[l]}$ should be initialized randomly to break symmetry. 
- It is however okay to initialize the biases $b^{[l]}$ to zeros. Symmetry is still broken so long as $W^{[l]}$ is initialized randomly. 

**In summary**:
- Initializing weights to very large random values does not work well. 
- Hopefully intializing with small random values does better. The important question is: how small should be these random values be? Lets find out in the next part! 

"He Initialization"; this is named for the first author of He et al., 2015. (If you have heard of "Xavier initialization", this is similar except Xavier initialization uses a scaling factor for the weights $W^{[l]}$ of `sqrt(1./layers_dims[l-1])` where He initialization would use `sqrt(2./layers_dims[l-1])`.)




**What is L2-regularization actually doing?**:

L2-regularization relies on the assumption that a model with small weights is simpler than a model with large weights. Thus, by penalizing the square values of the weights in the cost function you drive all the weights to smaller values. It becomes too costly for the cost to have large weights! This leads to a smoother model in which the output changes more slowly as the input changes. 


the implications of L2-regularization on:
- The cost computation:
    - A regularization term is added to the cost
- The backpropagation function:
    - There are extra terms in the gradients with respect to weight matrices
- Weights end up smaller ("weight decay"): 
    - Weights are pushed to smaller values.


When you shut some neurons down, you actually modify your model. The idea behind drop-out is that at each iteration, you train a different model that uses only a subset of your neurons. With dropout, your neurons thus become less sensitive to the activation of one other specific neuron, because that other neuron might be shut down at any time.


<font color='blue'>

**What you should remember about dropout:**
- Dropout is a regularization technique.
- You only use dropout during training. Don't use dropout (randomly eliminate nodes) during test time.
- Apply dropout both during forward and backward propagation.
- During training time, divide each dropout layer by keep_prob to keep the same expected value for the activations. For example, if keep_prob is 0.5, then we will on average shut down half the nodes, so the output will be scaled by 0.5 since only the remaining half are contributing to the solution. Dividing by 0.5 is equivalent to multiplying by 2. Hence, the output now has the same expected value. You can check that this works even when keep_prob is other values than 0.5.  