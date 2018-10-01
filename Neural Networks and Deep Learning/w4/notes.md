## DNN

vectorized sample: stack samples horizontally.

activation veter = [number of units in this layer, 1]

$W^l = [n^l, n ^{l-1}]$
$b^l = [n^l, 1]$
$dW.shape = W.shape$
$db.shape = b.shape$


in vectorized version, W, b, dW, db are the same dimension, but Z and A, X are changed (b remains the same size as python will use broadcasting automatically when adding)


Why DNN works better than shallow one?

1st layer: try to find edges
2nd: group edges together to see diff. parts of faces
3rd: group parts to see faces.

Hyperparameters: the param. influence the W and b


best hyperparam. can be differ as different architecture of GPU/CPU etc.



CODING TIPS:

**A few types of images the model tends to do poorly on include:** 
- Cat body in an unusual position
- Cat appears against a background of a similar color
- Unusual cat color and species
- Camera Angle
- Brightness of the picture
- Scale variation (cat is very large or small in image) 