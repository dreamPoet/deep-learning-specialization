## precision and recall

precision: how many of classified cats are real cats
recall: how many of real cats are classified as cat


P = TP / (TP + FP)
R = TP / (TP + FN)
FP = Type I error
FN = Type II error

F1 Score = harmonic mean of R and P ; 2 /(1/P + 1/R) = 2PR / (P+R)

---

Set one as optimizing metric and the other as satisficing metric.

set dev and test on the same dist.

test set for unbias testing; the dataset used for tuning is dev in fact.

dev is used to compare A and B models; test is used to do the final evaluation

when metrics cannot give correct order preference of algorithms, change it.

---
bayes (optimial) error: the theoritical best performance mapping form X to Y

reasons: noise; to blur to tell.

model improve small after exceeding human performance

1. human performance is very close to bayes error, so there is not too much room to improve
2. before exceeding, there are lots of tools to improve; after it, it is harder 


people are good at natural perception task.

structured data: data that has a defined length and format for big data, eg: numbers, dates, it can be stored in a database

unstructured data:books, documents, audio, video, images, emails.

