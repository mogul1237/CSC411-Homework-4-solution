# CSC411-Homework-4-solution

Download Here: [CSC411 Homework 4 solution](https://jarviscodinghub.com/assignment/csc411-homework-4-solution/)

For Custom/Original Work email jarviscodinghub@gmail.com/whatsapp +1(541)423-7793

1. [4pts] AlexNet. For this question, you will first read the following paper:
A. Krizhevsky, I. Sutskever, and G. E. Hinton. ImageNet classification with deep
convolutional neural networks. In Advances in Neural Information Processing Systems (NIPS), 2012.
https://papers.nips.cc/paper/4824-imagenet-classification-with-deep-convolutional-neural-networks
This is a highly influential paper (over 35,000 citations on Google Scholar!) because it was one
of the first papers to demonstrate impressive performance for a neural network on a modern
computer vision benchmark. It generated lots of excitement both in academia and in the
tech industry. The architecture presented in this paper widely used today, and is known as
“AlexNet”, after the first author. Reading this paper will also help you review a lot of the
important concepts from this class.
(a) [3pts] They use a conv net architecture which has five convolution layers and three fully
connected layers (one of which is the output layer). Your job is to count the number
of units, the number of weights, and the number of connections in each layer. I.e., you
should complete the following table:
# Units # Weights # Connections
Convolution Layer 1
Convolution Layer 2
Convolution Layer 3
Convolution Layer 4
Convolution Layer 5
Fully Connected Layer 1
Fully Connected Layer 2
Output Layer
You can ignore the pooling layers when doing these calculations, i.e. you don’t need
to consider the units in the pooling layers or the connections between convolution and
pooling layers. You can also ignore the biases. Note that the paper gives you the answers
1
https://markus.teach.cs.toronto.edu/csc411-2019-01
2
https://www.cs.toronto.edu/~mren/teach/csc411_19s/syllabus.pdf
1
CSC411 Winter 2019 Homework 4
for the numbers of units in the caption to Figure 2. Therefore, we won’t mark the column
for units, though you would benefit from trying to work it out yourself.
When counting the number of connections, we’ll adopt the convention that when the
input to a convolution layer is zero-padded, the connections to the dummy zero values
count towards the total. (This is the most convenient way to do it, since it means the
number of incoming connections is the same for each unit in a given layer.)
(b) [1pt] Now suppose you’re working at a software company and want to use an architecture similar to AlexNet in a product. Your project manager gives you some additional
instructions; for each of the following scenarios, based on your answers to Part 1, suggest
a change to the architecture which will help achieve the desired objective. E.g., modify
the sizes of one or more layers. (These scenarios are independent.)
i. You want to reduce the memory usage at test time so that the network can be run
on a cell phone; this requires reducing the number of parameters for the network.
ii. Your network will need to make very rapid predictions at test time. You want to
reduce the number of connections, since there is approximately one add-multiply
operation per connection.
2. [5pts] Gaussian Na¨ıve Bayes. In this question, you will derive the maximum likelihood
estimates for Gaussian Na¨ıve Bayes, which is just like the na¨ıve Bayes model from lecture,
except that the features are continuous, and the conditional distribution of each feature given
the class is (univariate) Gaussian rather than Bernoulli. Start with the following generative
model for a discrete class label y ∈ (1, 2, …, K) and a real valued vector of D features x =
(x1, x2, …, xD):
p(y = k) = αk (1)
p(x|y = k, µ,σ) = Y
D
d=1
2πσ2
d
!−1/2
exp (
−
X
D
d=1
1
2σ
2
d
(xd − µkd)
2
)
(2)
where αk is the prior on class k, σ
2
d
are the variances for each feature, which are shared
between all classes, and µkd is the mean of the feature d conditioned on class k. We write
α to represent the vector with elements αk and similarly σ is the vector of variances. The
matrix of class means is written µ where the kth row of µ is the mean for class k.
(a) [1pt] Use Bayes’ rule to derive an expression for p(y = k|x, µ,σ). Hint: Use the law of
total probability to derive an expression for p(x|µ,σ).
(b) [1pt] Write down an expression for the negative likelihood function (NLL)
`(θ; D) = − log p(y
(1)
, x
(1), y(2)
, x
(2)
, · · · , y(N)
, x
(N)
|θ) (3)
of a particular dataset D = {(y
(1)
, x
(1)),(y
(2)
, x
(2)), · · · ,(y
(N)
, x
(N)
)} with parameters
θ = {α, µ,σ}. (Assume the data are i.i.d.) You may find it helpful to use the indicator
notation I[y
(n) = k].
(c) [2pts] Take partial derivatives of the likelihood with respect to each of the parameters
µkd and with respect to the shared variances σ
2
d
. Based on this, find the maximum
likelihood estimates for µ and σ. You may assume that each class appears at least once
in the dataset. You may use the notation Nk =
PN
n=1 I[y
(n) = k] in your answers.
2
CSC411 Winter 2019 Homework 4
(d) [1pt] Show that the MLE for αk is given by the following equation:
αk =
1
N
X
N
n=1
I[y
(n) = k] = Nk
N
(4)
You may assume that each class appears at least once. You will find it helpful to read
about Lagrange multipliers3
.
3
https://en.wikipedia.org/wiki/Lagrange_multiplier
