## Face recognition

verification: 1to1 problem

recognition: much harder; K people = K times error prob. than verification.

triplet loss: A, P, N

add a margin to avoid learning param. let all encoding be 0. add a hyperparam. 

binary classification: still use siamese network; store the encoding of imgs in database(precomputing)


## Neural style transfer

content + style


correlation btw channels: occer together

style matrx = gram matrix




TIPS:

here're some ways to further improve the algorithm:
- Put more images of each person (under different lighting conditions, taken on different days, etc.) into the database. Then given a new image, compare the new face to multiple pictures of the person. This would increae accuracy.
- Crop the images to just contain the face, and less of the "border" region around the face. This preprocessing removes some of the irrelevant pixels around the face, and also makes the algorithm more robust.


**What you should remember**:
- Face verification solves an easier 1:1 matching problem; face recognition addresses a harder 1:K matching problem. 
- The triplet loss is an effective loss function for training a neural network to learn an encoding of a face image.
- The same encoding can be used for verification and recognition. Measuring distances between two images' encodings allows you to determine whether they are pictures of the same person. 




One important part of the gram matrix is that the diagonal elements such as  GiiGii  also measures how active filter  ii  is. For example, suppose filter  ii  is detecting vertical textures in the image. Then  G_{ii}  measures how common vertical textures are in the image as a whole: If  GiiGii  is large, this means that the image has a lot of vertical texture.

<font color='blue'>
**What you should remember**:
- The style of an image can be represented using the Gram matrix of a hidden layer's activations. However, we get even better results combining this representation from multiple different layers. This is in contrast to the content representation, where usually using just a single hidden layer is sufficient.
- Minimizing the style cost will cause the image $G$ to follow the style of the image $S$. 
</font color='blue'>




<font color='blue'>
What you should remember:
- Neural Style Transfer is an algorithm that given a content image C and a style image S can generate an artistic image
- It uses representations (hidden layer activations) based on a pretrained ConvNet. 
- The content cost function is computed using one hidden layer's activations.
- The style cost function for one layer is computed using the Gram matrix of that layer's activations. The overall style cost function is obtained using several hidden layers.
- Optimizing the total cost function results in synthesizing new images. 
