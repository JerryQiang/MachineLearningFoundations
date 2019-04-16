[TOC]

# Lecture 2: Learning to Answer Yes/No
## Perceptron Hypothesis Set

For $x = (x_1 ,x_2 ,··· ,x_d )$ ‘features of sample’, compute a weighted ‘score’($\sum_{i=1}^{d}w_ix_i>threshold$)
and approve credit if score>threshold, deny credit if score>threshold and ignore the equals.
$Y:\{+1,  -1\}$:
$$
h(x)=sign((\sum_{i=1}^{d}w_ix_i)-threshold) \stackrel{w_0 = -threshold, x_0 = +1}{\xlongequal{\quad\quad\quad}}
\\sign((\sum_{i=1}^{d}w_ix_i)+w_0*x_0) = sign((\sum_{i=0}^{d}w_ix_i)) = sign(w^Tx)
$$
called ‘**perceptron**’ hypothesis historically
<br/>

### Perceptrons in $R^2$
![Perceptrons in 2D](E:\学习笔记\mkdocs\MachineLearning\docs\Foundations\resources\imgs\Lecture 2 Learning to Answer Yes or No\2D Perceptrons.png)

<br/>

**perceptrons（感知器） ⇔  linear (binary) classifiers**




<br/>

### Fun Time
**Consider using a perceptron to detect spam messages.**
Assume that each email is represented by the frequency of keyword
occurrence, and output +1 indicates a spam. Which keywords below
shall have large positive weights in a good perceptron for the task?
1.&nbsp;coffee, tea, hamburger, steak
2.&nbsp;**free, drug, fantastic, deal** &nbsp;$\checkmark$
3.&nbsp;machine, learning, statistics, textbook
4.&nbsp;national, Taiwan, university, coursera

**Explanation**
垃圾邮件常含"免费",''打折","好消息"等词。
<br/>



## Perceptron Learning Algorithm (PLA)
​	correct mistakes and improve iteratively
## Guarantee of PLA
	no mistake eventually if linear separable
## Non-Separable Data
	hold somewhat ‘best’ weights in pocket

## Summary
### 讲座总结
Perceptron Hypothesis Set
	hyperplanes/linear classifiers in $R_d$
Perceptron Learning Algorithm (PLA)
​	correct mistakes and improve iteratively
Guarantee of PLA
	no mistake eventually if linear separable
Non-Separable Data
	hold somewhat ‘best’ weights in pocket