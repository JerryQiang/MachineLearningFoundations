[TOC]
<br/>

# Lecture 6: Theory of Generalization
<br/>

## Restriction of Break Point
<br/>
![The Four Break Points](E:\学习笔记\mkdocs\MachineLearning\docs\Foundations\resources\imgs\Lecture 6 Theory of Generalization\four_break_points.png)
<br/>

![N=3, K=2 Break Point](E:\学习笔记\mkdocs\MachineLearning\docs\Foundations\resources\imgs\Lecture 6 Theory of Generalization\break_point.png)
<br/>
$$
\begin{aligned} & m_{\mathcal{H}}(N) \\ \leq & \text { maximum possible } m_{\mathcal{H}}(N) \text { given } k \\ \leq & p o l y(N) \end{aligned}
$$

### Fun Time
When minimum break point k = 1, what is the maximum possible $m_{\mathcal{H}}(N)$ when $N = 3$？
1.&nbsp; **1**&nbsp;$\checkmark$&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp; 2.&nbsp;2&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;3.&nbsp;3&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp; 4.&nbsp;4
<br/>
**Explanation**
因为$k=1$，所以没有任何一个点可以和它共存，所以$m_H (N) = 1$
<br/>


## Bounding Function: Basic Cases
<br/>

### Bounding Function

bounding function $B(N,k)$:
&emsp;&emsp;maximum possible $m_H (N)$ when break point = k
$$
B(N, k) \leq p o l y(N)
$$

换言之，$B(N, k)$是$m_H (N)$的**上界**。 

<br/>

### Table of Bounding Function
![Table of Bounding Function](E:\学习笔记\mkdocs\MachineLearning\docs\Foundations\resources\imgs\Lecture 6 Theory of Generalization\bounding _function_table.jpg)
<br/>

### Fun Time
For the **2D perceptrons**, which of the following claim is true?
1 minimum break point k = 2
2 $m_{\mathcal{H}}(4)$= 15
3 $m_{\mathcal{H}}(N)<B(N, k)$ when $N = k = $ minimum break point &nbsp;$\checkmark$
4 $m_{\mathcal{H}}(N)>B(N, k)$ when $N = k = $ minimum break point
<br/>
**Explanation**
minimum break point k = 3
$m_{\mathcal{H}}(4)$= 14
$B(N, k)$是$m_H (N)$的**上界**
不记得**2D感知器**的同学，可以回顾Lecture 5: Training versus Testing中的Effective Number of Hypotheses :-)
<br/>

## Bounding Function: Inductive Cases
<br/>

$$
B(4,3)=11=2 \alpha+\beta
$$

![Instance Estimating Part](E:\学习笔记\mkdocs\MachineLearning\docs\Foundations\resources\imgs\Lecture 6 Theory of Generalization\instance_estimating_part.png)
<br/>
$$
\begin{aligned} B(N, k) &=2 \alpha+\beta \\ \alpha+\beta & \leq B(N-1, k) \\ \alpha & \leq B(N-1, k-1) \\ \Rightarrow B(N, k) & \leq B(N-1, k)+B(N-1, k-1) \end{aligned}
\\ B(N, k) \leq \sum_{i=0}^{k-1} \left( \begin{array}{c}{N} \\ {i}\end{array}\right)
$$
![The Upper Bound of Bounding Function](E:\学习笔记\mkdocs\MachineLearning\docs\Foundations\resources\imgs\Lecture 6 Theory of Generalization\bounding_function_upperbound].png)

$\le$ **实际上是**$=$
即
$$
B(N, k) = B(N-1, k)+B(N-1, k-1)
\\ B(N, k) = \sum_{i=0}^{k-1} \left( \begin{array}{c}{N} \\ {i}\end{array}\right) = C_N^0+C_N^1 +...+C_N^{k-1}  
$$

![The Three Break Points](E:\学习笔记\mkdocs\MachineLearning\docs\Foundations\resources\imgs\Lecture 6 Theory of Generalization\three_break_points.png)
<br/>

### Fun Time
For **1D perceptrons** (positive and negative rays), we know that $m_H (N)$ = 2N. Let k be the minimum break point. Which of the following is not true?
1 k = 3
2 for some integers $N>0 ,\ m_{\mathcal{H}}(N)=\sum_{i=0}^{k-1} \left( \begin{array}{c}{N} \\ {i}\end{array}\right)$
3 for all integers $N>0 ,\ m_{\mathcal{H}}(N)=\sum_{i=0}^{k-1} \left( \begin{array}{c}{N} \\ {i}\end{array}\right)$ &nbsp;$\checkmark$
4 for all integers $N>2 ,\ m_{\mathcal{H}}(N)<\sum_{i=0}^{k-1} \left( \begin{array}{c}{N} \\ {i}\end{array}\right)$
<br/>
**Explanation**
minimum break point k = 3
$B(N, k) = \sum_{i=0}^{k-1} \left( \begin{array}{c}{N} \\ {i}\end{array}\right)$
$B(N, k)$是$m_H (N)$的**上界**，当N$\ge$k时，$m_H (N)<B(N, k)$; 当N$<$k时，$m_H (N)=B(N, k)$.
<br/>
拓展：回顾下Lecture 5: Training versus Testing中的Effective Number of Hypotheses Funtime
求2维感知器中5个点的有效分类数(k=3,N=5 $m_{\mathcal{H}}(N)=? \leq \frac{1}{6} N^{3}+\frac{5}{6} N+1$)，N>k，=取不到。
正确答案22<($\frac{125}{6}+\frac{25}{6}+1=25$)，验证成功，回顾题目也挺有趣味的。:-)

<br/>





## A Pictorial Proof

![Step 1: Replace E_out by E_in'](E:\学习笔记\mkdocs\MachineLearning\docs\Foundations\resources\imgs\Lecture 6 Theory of Generalization\step1.png)
<br/>

用$E_{in}'$（有限）替换$E_{out}$(无限)，但是这个不等式及$\frac{1}{2}$的系数的出处，我没想明白。



![Step 2: Decompose H by Kind](E:\学习笔记\mkdocs\MachineLearning\docs\Foundations\resources\imgs\Lecture 6 Theory of Generalization\step2.png)
<br/>

将上界定义为以$m_{H}(2N)$为基准的。



![Step 3: Use Hoeffding without Replacement](E:\学习笔记\mkdocs\MachineLearning\docs\Foundations\resources\imgs\Lecture 6 Theory of Generalization\step3.png)
<br/>

使用无放回的霍夫丁不等式，结果类似，只是$\nu=E_{\text { in }},\mu=\frac{E_{\text { in }}+E_{\text { in }}^{\prime}}{2}$。



### Vapnik-Chervonenkis (VC) bound

$$
\begin{aligned}
& \mathbb{P}\left[\exists h \in \mathcal{H} \text { s.t. } | E_{\text { in }}(h)-E_{\text { out }}(h) |>\epsilon\right] \\ & \leq  4 m_{\mathcal{H}}(2 N) \exp \left(-\frac{1}{8} \epsilon^{2} N\right) \end{aligned}
$$
&emsp;&emsp;$m_H (N)$ can replace M with a few changes
<br/>


## Summary
本篇讲义主要讲了Bound Function$B(N,k)$以及VC Bound的含义及推导。

<br/>

### 讲义总结


<br/>

**Restriction of Break Point**
&emsp;&emsp;break point ‘breaks’ consequent points
<br/>

**Bounding Function: Basic Cases**
&emsp;&emsp;$B(N,k)$ bounds $m_H (N)$ with break point k
<br/>

**Bounding Function: Inductive Cases**
&emsp;&emsp;$B(N,k)$ is poly(N)
<br/>

**A Pictorial Proof**
&emsp;&emsp;$m_H (N)$ can replace M with a few changes
<br/>

### 参考文献
<a href="https://www.csie.ntu.edu.tw/~htlin/course/mlfound18fall/">《Machine Learning Foundations》(机器学习基石)—— Hsuan-Tien Lin (林轩田)</a>