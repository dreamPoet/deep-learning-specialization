## error analysis

do human analysis on where the error is can help you find where you should real spend time on.

random incorrectly labeled data in train set is OK, DL are robust to random errors but not systematic error(eg: always label white dog as cat)

in dev test, can also count mislabedl data to help check the error analysis. If it does  affect evaluation, correct it. EG:  10% ONLY 0.6% from mislabeled, acceptable; 2% on val where 0.6% mislabeled, it should be corrected(as if you have two models on val: 2% and 2.1%, we cannot say which one is better consider the mislabeled data).

check both samples got right and got wrong to avoid bias if only check wrong samples.(not easy to do)

correct label in trainning set is not so important. trainning set can from different dist. with dev/test


## mismatched train and dev/test

1. put all data together and do shuffle.
- disadv: the test/dev will come from the dataset which is the major one.
- 2. training on the major one and some of the target one, dev/test are from target dataset.
- disadv: training dist is diff from dev/test


variance problem may because of mismatch data dist of train and dev/test

to make sure whether it is high variance or not: do error analysis on a train-dev dataset separated from the original training set. Use the rest of training set as the new training set. To distinguish variance problem or data mismatch(training on diff dist) problem

may also exist overfit to dev set(add more samples to dev set)


no systems way to deal with data dismatch.
1. observe how difference btw two sets, try to make them similar.

artificial data synthesis: do not repeat noise data and adding it to the original directly, it may cause overfit on these noise which is just a subset of the real noise, although human will think it OK to simulate the real world.


## learning from multi tasks

transfer learning: use a pretrained NN and discard the final layer with its weights, initialize it(W^L), retrain on the new data set.

If your new dataset is big enough, can retrain wall the param. of NN. <- the first stage is called **pre-training**. Params are **pre-initailize**. this new train stage is called **fine tuning**


The reason is, the low layer features, what you learned like edges curves from large dataset, help it do better in new img.

multi-task learning can also share some low features when learning, which speed up the solution. some images are not Fully labeled can also train a target NN(a image has car + stop sign but only label the car and ? for stop sign); multi-task learning need a big enough NN.


## end-to-end DL

challenge: need big data; 

for small dataset, human designed components might be helpful. but it also may enforce machine learning human knowledge which might be harmful.





Interesting area: DRL; NLP; One-shot/transfer. unsupervised.


QUIZ 10:

artificial imgs combining foggy and roads:

This is because biologically human vision sensory is more complex than our hearing sensory thus our eyes enable us to perform a far more deeper sight understanding than computer vision can, such as understanding depth in a image. Therefore, human-level performance can be used as a proxy for Bayes error for images.

But human hearing sensory is not as complexly built as our vision, and computer can already bypass human level performance, therefore, we can't use human hearing performance as a proxy for Bayes error for audio.

----

In the video lecture "Addressing data mismatch" under "Artificial data synthesis" section, Prof. Ng talked about the 10,000 hours of audio clips synthesized with only 1 hour of car noise, which has ratio of 0.01%, could run into the risk of overfitting to that 1 hour of car noise. The concern of overfitting here is that human hearing sense is not as sharp as human eyes, although we can hear the car noise in the synthesized audios, but we can't assume human audio sense error to be close to Bayes error.

Another example of overfitting from the lecture with human vision is using 20 car images extracted from video game to simulate large number of cars as part of training dataset for self-driving cars. This could also run into the risk of overfitting to that 20 video car images, albeit human visual sense is shaper, seeing them as realistic cars and human visual error can be viewed as Bayes error. The overfitting here is because that 20 car images used for generating artificial data is still too small a ratio comparing to the number of realistic variety of cars. That is, the subset of cars used to synthesize is too small, while the total space of the cars is a lot more bigger, thus runs the risk of overfitting.

However, in Question 10 we have 1,000,000 images from front-facing camera, and 1000 synthesized fog images, which has ratio of 0.1%, that is, the subspace used for synthesize is much larger than 0.01% for the audio, or 20 artificial car images as mentioned above. As human eyes are shaper and if these 1,000 synthesized foggy images look realistic to human eyes, we can assume human error on these synthesized images is the same or very close to Bayes error, thus we can have high confidence that those synthesized foggy images do reflect the distribution of real foggy images.

In brief, 2 key points why the answer is correct: 1). Having big enough, but not too small number of synthesized fog images. 2). Human error on viewing images can be treated as Bayes error. These 2 points give us confidence that the 1000 synthesized images do reflect the distribution of the real foggy images.