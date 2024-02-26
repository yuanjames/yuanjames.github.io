---
layout: post
comments: true
title : PyGlove - Symbolic Programming for Automated Machine Learning
categories: paper-review
date: 2021-1-8 12:00:00
---

In this paper, they introduce a new way of programming AutoML based on symbolic programming. Under this paradigm, ML programs are mutable, thus can be manipulated easily by another program. As a result, AutoML can be reformulated as an automated process of symbolic manipulation.

![PyGlove](/pics/PyGlove.jpg)

An analogy to this process is to have a robot build a house with LEGO bricks to meet a human being’s taste: symbolizing a regular program is like converting molded plastic parts into LEGO bricks; hyperifying a symbolic program into a search space is like providing a blueprint of the house with variations. With the help of the search algorithm, the search space is materialized into different child programs whose rewards are fed back to the search algorithm to improve future sampling, like a robot trying different ways to build the house and gradually learning what humans prefer.

From my perspective, PyGlove is similar to [Optuna](https://optuna.org/). They both proposed the idea and framework to do hyperparameters search.


ref: https://proceedings.neurips.cc/paper/2020/file/012a91467f210472fab4e11359bbfef6-Paper.pdf