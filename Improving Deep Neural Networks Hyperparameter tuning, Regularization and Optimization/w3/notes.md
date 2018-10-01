## hyperparam.

important: 

alpha;

momentum beta; mini-batch size; num. hidden units

num. layers; learning rate decay.

log scale.

for beta, when beta close to 1, small change will have huge effect. use 1-beta make it chooses more values in beta close to 1 (1-beta close to 0).

babysitting one model: not enough computation sourse.


## batch normalization

normalize all layers A(or Z)

we do normalization on Z here.

as in batch norm, doing the normalization willsubstract the b (computing mean of the Z), so add whatever b will not influence the Z-tiled. To summary, BN make Z in each layer has mean 0, so b can be omited while only beta is remained to control the shift or bias terms.

beta and gamma have the same dimension with Z, (n, 1)


due to the covariance shift, changes on input distrubtion will influence the learning of the param. for hidden units, the input A is always change. do batch norm helps reduce the influence of this distribute change. It makes the mean and variance of input Z remains the same (control by beta and gamma).

beta and gamma limit the update of param in the previous layer which can affect the dist. of values the hidden layer sees. BN allow each layer learn by itself, becomes more independent.

BN has very little regularization as it introduce noise by 1. compute on mini batch 2. mean and variance computing error, make later layers do not depend on the previous layer input. dropout make layers do not depend on previous input by multiply neurons with 0 or 1.

larger mini batch size will reduce the regularization effect of BN.

Use BN to speed up learning.


** in test time** there is no mini batch and we deal with one sample in a time. so we use exponentially weighted avg. across the mini batch.


## multi-class

softmax regression: decision boundary btw two class are still linear.

softmax NN: non linear.


hardmax: for the largest elem. set as 1, others set as 0.



## TF

placeholder: feed training data
Variable: the param. need train.


**To summarize, you how know how to**:

1. Create placeholders
2. Specify the computation graph corresponding to operations you want to compute
3. Create the session
4. Run the session, using a feed dictionary if necessary to specify placeholder variables' values. 