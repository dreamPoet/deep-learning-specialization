1.as most of kernel are symmetric, so we do not do the reverse.
2. what we done in ML called COV is cross-correlation in fact. real cov(with flapping) has (A*B)*C = A*(B*C) associtivity rule.

sobel: 1 2 1
scharrL 3 10 3

we can just set these as weights we want to learn

padding: 1. shrinky output 2. throw away info in edges.

same conv: p = (f -1) /2
valid conv: p = 0

in CV, f is usually odd.


output = floor((n + 2p - f)/s) + 1

the conv must in the img, so do floor. 

depth = channels, the 3rd dimension of volumes.

we call g as activation func. as it outputs activation for next layer


the size of input does not influence the number of param. as the number of param. is small compared with the input img size, so it is less possible to overfit.

pooling layer also has f and s as hyperparam. look at an activation layer, a large number means it may detect some specific feature, max pooling just keep this number. pooling keep the same channel as input. it done independently.

avg pooling used to keep features of a area.

pooling and conv can be called as one layer as we recard a layer as which have params, where pooling does not have param. need to learn.


does not use hyperparam. created by yourself, use that work good in other papers.

ADV: param. sharing & sparse connectivies.

translation invariance.



QUIZ:

In lecture we talked about “parameter sharing” as a benefit of using convolutional networks. Which of the following statements about parameter sharing in ConvNets are true? (Check all that apply.)


It reduces the total number of parameters, thus reducing overfitting.


X It allows gradient descent to set many of the parameters to zero, thus making the connections sparse.


X It allows parameters learned for one task to be shared even for a different task (transfer learning).


It allows a feature detector to be used in multiple locations throughout the whole input image/input volume.
