[TOC]

# Lecture 3: Types of Learning
## Learning with Different Output Space $Y$
基于输出空间是否为**数值**，数值是否**连续**分类。
&emsp;&emsp;数值离散为分类学习(classification)
&emsp;&emsp;&emsp;&emsp;二分类(binary classification ) $Y = \{−1,+1\}$&emsp;i.e. patient features ⇒ sick or not
&emsp;&emsp;&emsp;&emsp;多分类(multiclass classification)  $Y = \{1,2, ..., K\}$&emsp; i.e. patient features ⇒ which type of cancer;
&emsp;&emsp;数值连续为回归学习(regression)  $Y = R$&emsp; i.e. patient features ⇒ how many days before recovery;
&emsp;&emsp;非数值为结构学习（structured）$Y = structures​$&emsp; i.e. patient features ⇒ order of illness. 
&emsp;&emsp;补充：结构学习学习到的可能是树结构（i.e.决策树）、向量（i.e. 得病顺序，句子结构）等结构。 
<br/>

### Fun Time
**What is this learning problem?**
**The entrance system of the school gym, which does automatic face recognition based on machine learning, is built to charge four different groups of users differently: Staff, Student, Professor, Other. What type of learning problem best fits the need of the system?**
1 binary classification
2 **multiclass classification** &nbsp;$\checkmark​$
3 regression
4 structured learning
<br/>
**Explanation**
结果分成四类：Staff, Student, Professor, Other. 
很明显是**多分类学习问题**。
<br/>

## Learning with Different Data Label $y_n$
<br/>
基于样本数据有**多少标签**，标签是否为**数值**分类。
&emsp;&emsp;全部样本数据有标签为监督学习(supervised) all $y_n$
&emsp;&emsp;部分/无样本数据有标签为半/无监督学习(semi/un-supervised) some/no $y_n$
&emsp;&emsp;标签是局部不明确的信息为强化学习(reinforcement)  implicit $y_n$ by goodness($\tilde{y}_n$)
<br/>

### Fun Time
**What is this learning problem?**
**To build a tree recognition system, a company decides to gather one million of pictures on the Internet. Then, it asks each of the 10 company members to view 100 pictures and record whether each picture contains a tree. The pictures and records are then fed to a learning algorithm to build the system. What type of learning problem does the algorithm need to solve?**
1 supervised
2 unsupervised
3 **semi-supervised** &nbsp;$\checkmark$
4 reinforcement
<br/>
**Explanation**
总共1 million pictures，标注了 10\*100 = 1000张图片
很明显是半监督学习。
<br/>



## Learning with Different Protocol $f ⇒ (x_n ,y_n )$
基于样本学习的方式分类。
&emsp;&emsp;直接用所有数据学习的是批处理学习(batch) **填鸭式教育，一次性灌输。**
&emsp;&emsp;数据逐步接受，逐步学习的是在线学习(online) **被动学习，每天学一点。**
&emsp;&emsp;主动选择学习的数据的是主动学习(active) **主动学习，直接向老师请教。**
<br/>

### Fun Time
**What is this learning problem?**
**A photographer has 100,000 pictures, each containing one baseball player. He wants to automatically categorize the pictures by its player inside. He starts by categorizing 1,000 pictures by himself, and then writes an algorithm that tries to categorize the other pictures if it is ‘confident’ on the category while pausing for (& learning from) human input if not. What protocol best describes the nature of the algorithm?**
1 batch
2 online
3 **active** &nbsp;$\checkmark​$
4 random
<br/>
**Explanation**
100,000 pictures, 自己标注了1000张图片，然后写了个算法让程序提出它不确信的图片，再人工标注这些图片。
很明显是主动学习。
<br/>



## Learning with Different Input Space $X$
基于输入空间的特征分类。
&emsp;&emsp;基于简单有具体含义特征的学习称为原始学习(raw)
&emsp;&emsp;基于复杂有具体含义特征的学习称为具体学习(concrete)
&emsp;&emsp;基于几乎没有具体含义特征的学习称为抽象学习(abstract) 
$$
raw \ features
\\ \quad\quad\quad\quad\quad conversion/ \Downarrow  extraction/construction
\\ concrete \ features
\\ \quad\quad \Downarrow  again
\\abstract \ features
$$
按照我的理解是一开始数据的特征就是**原始**的，通过初步**转换/抽取/构造**为**具体**的，再进一步就是**抽象**特征。
拿数字识别来举例，直接输入的图片像素就是原始特征；我们利用数字的对称性和稀疏性，将像素进行处理，得到的是具体特征；再进一步用一个神经网络训练得到多分类器（多分类器模型的每层输入就是下一层的抽象特征输入）。
<br/>

### Fun Time
**What features can be used?**
**Consider a problem of building an online image advertisement system that shows the users the most relevant images. What features can you choose to use?**
1 concrete
2 concrete, raw
3 concrete, abstract 
4 **concrete, raw, abstract** &nbsp;$\checkmark​$
<br/>
**Explanation**
all of them above!
raw features: image pixels
concrete features: the feature of image advertisement system
abstract features: the pattern of image advertisement system 
可以提取不同的特征输入，再用相关的算法学习。
<br/>


## Summary
### 讲义总结
本次讲义主要讲述了不同类型的学习。基于不同角度有不同的分类，其中**[]**为本门课学习和接触的，后面的更难，也更接近现实需求。
**Learning with Different Output Space** $Y$
&emsp;&emsp;[classification], [regression], structured
<br/>

**Learning with Different Data Label** $y_n​$
&emsp;&emsp;[supervised], un/semi-supervised, reinforcement
<br/>

**Learning with Different Protocol** $f ⇒ (x_n ,y_n )​$
&emsp;&emsp;[batch], online, active
<br/>

**Learning with Different Input Space** $X​$
&emsp;&emsp;[concrete], raw, abstract
<br/>


### 参考文献
<a href="https://www.csie.ntu.edu.tw/~htlin/course/mlfound18fall/">《Machine Learning Foundations》(机器学习基石)—— Hsuan-Tien Lin (林轩田)</a>