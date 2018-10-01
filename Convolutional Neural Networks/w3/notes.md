## landmark detection

the order(what it means) of each landmark need to be same across the dataset.


## object detection

currently use convnet for each sliding window. Before we use mannual designed detection algo.


## conv

use 1x1xn_c filter equals to apply a linear mapping of the previous features, but only a set of them(f, f) instead of use all features in FC.


## YOLO

assign the object to the grid where objects' centre on.

usually use 19x19 grid; reduce the change one grid has multiply object.

very quick, can be use for real time.

## IoU

## NMS

do NMS on each class if multi-class

choose the highest, for others have high IoU, descards; repeat until loop all boxes.

## anchor boxes

for each object set a anchor boxes; in each label, set var for diff anchor boxes. Each object in training image is assigned to grid cell containing object's midpoint and anchor box for the grid cell with highest IoU.

disadv: 2 objects in one grid, similar to same anchor box: no way; do some tiebreaking.


**Summary for YOLO**:
- Input image (608, 608, 3)
- The input image goes through a CNN, resulting in a (19,19,5,85) dimensional output. 
- After flattening the last two dimensions, the output is a volume of shape (19, 19, 425):
    - Each cell in a 19x19 grid over the input image gives 425 numbers. 
    - 425 = 5 x 85 because each cell contains predictions for 5 boxes, corresponding to 5 anchor boxes, as seen in lecture. 
    - 85 = 5 + 80 where 5 is because $(p_c, b_x, b_y, b_h, b_w)$ has 5 numbers, and and 80 is the number of classes we'd like to detect
- You then select only few boxes based on:
    - Score-thresholding: throw away boxes that have detected a class with a score less than the threshold
    - Non-max suppression: Compute the Intersection over Union and avoid selecting overlapping boxes
- This gives you YOLO's final output. 



