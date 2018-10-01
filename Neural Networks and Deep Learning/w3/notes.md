## Shallow NN

we don't count input layer (a^0) as a layer when talk about representation of a NN.

Z/A/W: vertically: neurons/hidden units
horizontally: training samples



tanh func.: a shift version of sigmoid, (-1, 1)

$a = tanh(z)=(e^z-e^{-z})/(e^z+e^{-z})$

because with values between plus one and minus one, the mean of the activations are closer to having a zero mean. So just as sometimes when you train a learning algorithm, you might Center the data and have your data have zero mean using a tanh instead of a sigmoid function, which has the effect of centering your data so that the mean of the data is close to the zero rather than maybe a 0.5 and this actually makes learning for the next layer a little bit easier 

exception: if the y is {0, 1} and y_hat wanted is btw [0, 1], then use sigmoid instead of tanh for the output layer.


activation function can be differ for different layer.


use ReLU as the slope will be very small when z is very large or very small.

$a = max(0, z)$

derivative = 1 when z > 0 else derivative = 0 

when z = 0 the derivative does not existed, but we can get a very small number in practise. so we can pretend it as 0 or 1 when z = 0.



Rules:

always use ReLU on other hidden layer; when output layer is {0,1} use sigmoid.

disadv: z = 0(but ok in practise)

Leaky ReLU: better than ReLU, but not use much.

$a = max(0.01*z, z)$

adv: learning quiker than sigmoid


**why not just use identity/linear activation function?**

~= a logistic regression model without any hidden layer.


only use linear identical activation func. if output needs real number (price etc).

keepdims = True avoid ouput a rank 1 array


use random initialization to break symmetric; use small weights to avoid get a very large z which causes tanh or sigmoid GD very slow

0.01 weight is ok in a shadow NN; in DNN it cannot.


CODE TIPS:
W matrix : [output_units; input_units]
