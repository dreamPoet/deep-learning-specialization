## Intro to deep learning

### Housing price prediction

use regression to fit a straght line with 0 to replace the minus part.

size(x) -> neuron -> price(y)

neuron: max(0,y) ReLU: Rectified linearar Unite

stacking single neuron together to get a bigger neural network.


neural network itself decided which neuron takes which features and assign how much weights (density connected, all inputs are connected to all neurons).


structured data/unstructured data


on the small training sets, the performance of different algorithms are not decided. It's mainly depend on how well the features are extracted and details of the algorithm



on the sides of sigmoid, as the gradient are almost equals to 0, if using GD algorithm, it will be very slow in learning. Use ReLU, gradient descent will work much faster.