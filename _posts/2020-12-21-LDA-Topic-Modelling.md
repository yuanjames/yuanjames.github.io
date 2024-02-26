---
layout: post
comments: false
title : LDA Topic Modelling Explanation 
categories: knowlegde-note
date: 2020-12-21 12:00:00
---
Very simple, vivid explanation.
Here's link: https://www.youtube.com/watch?v=BaM1uiCpj_E&ab_channel=LuisSerrano


Main Equations (2 Dirichlet Distributions + 2 Multivariate Distribution):

For a document <a href="https://www.codecogs.com/eqnedit.php?latex=d" target="_blank"><img src="https://latex.codecogs.com/gif.latex?d" title="d" /></a> the distrbution for its topic <a href="https://www.codecogs.com/eqnedit.php?latex=\theta_{d}=\operatorname{Dirichlet}(\vec{\alpha})" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\theta_{d}=\operatorname{Dirichlet}(\vec{\alpha})" title="\theta_{d}=\operatorname{Dirichlet}(\vec{\alpha})" /></a>.

For a topic <a href="https://www.codecogs.com/eqnedit.php?latex=k" target="_blank"><img src="https://latex.codecogs.com/gif.latex?k" title="k" /></a> the distribution for the words is: <a href="https://www.codecogs.com/eqnedit.php?latex=\beta_{k}=\operatorname{Dirichlet}(\vec{\eta})" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\beta_{k}=\operatorname{Dirichlet}(\vec{\eta})" title="\beta_{k}=\operatorname{Dirichlet}(\vec{\eta})" /></a>.

Choose a topic, <a href="https://www.codecogs.com/eqnedit.php?latex=z_{d&space;n}=\operatorname{multi}\left(\theta_{d}\right)" target="_blank"><img src="https://latex.codecogs.com/gif.latex?z_{d&space;n}=\operatorname{multi}\left(\theta_{d}\right)" title="z_{d n}=\operatorname{multi}\left(\theta_{d}\right)" /></a>.

Choose a word, <a href="https://www.codecogs.com/eqnedit.php?latex=w_{d&space;n}=\operatorname{multi}\left(\beta_{z_{d&space;n}}\right)" target="_blank"><img src="https://latex.codecogs.com/gif.latex?w_{d&space;n}=\operatorname{multi}\left(\beta_{z_{d&space;n}}\right)" title="w_{d n}=\operatorname{multi}\left(\beta_{z_{d n}}\right)" /></a>.



The demo of using Gensim and PyLDAvis:
https://www.machinelearningplus.com/nlp/topic-modeling-gensim-python/