---
layout: post
comments: true
title: Ensemble Learning
categories: paper-review
date: 2020-12-22 12:00:00
---
Three representative methods: **Boosting**, **Bagging**, **Stacking**.Typically, an ensemble is constructed in two steps. First, a number of base learners are produced, which can be generated ina _parallel_ style or in a _sequential_ style where the generation of a base learner has influence on the generation of subsequent learners. Then, the base learners are combined to use, where among the most popular combination schemes are _majority voting_ for classification and _weighted averaging_ for regression.

**Boosting**: A single classifier may not be able to accurately predict the class of an object, but when we group multiple weak classifiers with each one progressively learning from the others' wrongly classified objects, we can build one such strong model. 

**Bagging**: Bagging trains a number of base learners each from a different bootstrap sample by calling a base learning algorithm.

**Stacking**: In a typical implementation of Stacking, a number of first-level individual learners are generated from the training data
set by employing different learning algorithms. Those individual learners are then combined by a second-level learner which
is called as meta-learner.

https://cs.nju.edu.cn/zhouzh/zhouzh.files/publication/springerEBR09.pdf