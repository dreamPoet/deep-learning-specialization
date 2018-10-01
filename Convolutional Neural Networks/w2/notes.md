## LeNet 6000params

use avg pooling and valid padding(=0)

does not use softmax; use sigmoid and tanh instead of relu.
diff. filters work on diff. channels due to limited computational sourse.
use non-linear.


## AlexNet 

60 milions params; trained on ImageNet; use ReLU; complex way to train on different GPU; use Local Response Nomalization layer.

LRN: for a volume, when look at one position, look through all channels of that position (H, W), to make not too many neurons have high activation value. it is not useful.


## VGG

use simple architectures,
 all CONV = 3x3,2=1,same; ALL pool = 2x2,s=2
 a deep network.

 VGG-16 and 19 perform almost the same.

 deeper, channels increase double, height and weight decrease half.



## ResNet

very deep NN is hard to train due to exploding and vanishing gradient problem <- skip connectiont

skip connection = shortcut

add previous layers A to later layers computation before ReLU


WHY it works?

1. add a^l to a^{l+2} when doing the ReLU helps shrink the value of w^{l+2} if we do L2 normalization
2. when w^{l+2} = 0, then it equals to g(a^l), so add these blocks will not hurt the performance. if they really learn something, then it helps.

Due to these addition operation, always use same conv. if not, use another w, which can be learned or just fixt for 0-padding to make same dimension.


1 by 1 cov = network in network

add non-linearity or reduce the number of channels.

this 1 by 1 used in inception model called as "bottleneck layer" to shrink the computation amount. Design it suitablly will not hurt the performance of NN.


it also use some side branches to predict what's the output label to prevent the overfitting. regularization.



1. Using Open-Source Implementation
2. Transfer Learning
- freeze all previous layers
- just train last layer ( change different softmax)
- save the activation(input) of the softmax to disk first, and then use these value to train softmax, so no need to compute again and again when training.
- if have larger dataset, freeze fewer layers.
- can drop up/use GD on pre-trained/create new layers.


Data agumentation:

change color according to some dist. (consider different light colour)

PCA colour agumentation: if image is mainly R B less G, PCA will add and substract lot on R B and do less on G.


ensembling: works for competition for better output.

ensembling need to keep all NNs while multi-crop does not.



identity block and conv block of ResNet.