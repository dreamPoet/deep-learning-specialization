## optimization algo.


SGD loose speedup from vectorization, although we can set a small learning rate to decrease the influence of noise.

use batch size 64, 128, 256, 512


exponentially weighted (moving) avg:

larger beta -> curve move to right and more smooth, the weight assigned to current day is less, it adapted more slowly.

for beta = 0.9, 0.9^10 = 1 / e ~= 0.3 of peak(weight of the current day, 1-beta = 0.1), it is quite small, so we say beta = 0.9 is the avg of 10 days.

(1-epsilon)^{1/epsilon} = 1/e

1/0.1 = 10 days

above are not formal expression.

use a window directly to compute avg are more accurate, but this method is much more effective

bias correction: divided by $1-\beta^t$ when t increase, this value will close to 1. It corrects the bias in the initial stage. but there is no need in real implementation.

### Root Mean Square prop

add a epsilon to the denumerator to avoid 0 and keep the numerical stability.

it allows to use a bigger learning rate; use the root square value to constrol the update speed of parameters.


### Adam optimization algo.

Adaptive moment estimation as dw is the first moment and dw^2 is the second moment

Adam and RMSprop are going to solving with plateaus.




**What you should remember**:

- Momentum takes past gradients into account to smooth out the steps of gradient descent. It can be applied with batch gradient descent, mini-batch gradient descent or stochastic gradient descent.
- You have to tune a momentum hyperparameter $\beta$ and a learning rate $\alpha$.