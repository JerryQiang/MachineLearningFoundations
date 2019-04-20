[TOC]
<br/>

# Lecture 5: Training versus Testing
<br/>

## Recap and Preview

![The Statistical Learning Flow](E:\学习笔记\mkdocs\MachineLearning\docs\Foundations\resources\imgs\Lecture 5 Training versus Testing\statistic_learning_flow.png)
<br/>

### Two Central Questions

![Two Central Questions](E:\学习笔记\mkdocs\MachineLearning\docs\Foundations\resources\imgs\Lecture 5 Training versus Testing\two_central_questions.png)
<br/>

&emsp;&emsp;**make sure that $E_{out} (g)$ is close enough to $E_{in} (g)$.**
&emsp;&emsp;**make  $E_{in} (g)$mall enough.**
<br/>

### Fun Time
Data size: how large do we need?
One way to use the inequality
$$
\mathbb{P}\left[ | E_{\text { in }}(g)-E_{\text { out }}(g) |>\epsilon\right] \leq \underbrace{2 \cdot M \cdot \exp \left(-2 \epsilon^{2} N\right)}_{\delta}
$$
is to pick a tolerable difference ? as well as a tolerable BAD probability δ, and then gather data with size (N) large enough to achieve those tolerance criteria. Let ? = 0.1, δ = 0.05, and M = 100.
What is the data size needed?
1.&nbsp; 215 &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp; 2.&nbsp;**415** &nbsp;$\checkmark$&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;3.&nbsp;615&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp; 4.&nbsp;815
<br/>
**Explanation**
$N=\frac{1}{2 \epsilon^{2}} \ln \frac{2 M}{\delta}$
所以$N =414.7  \approx 415$
<br/>




## Effective Number of Lines

###  Uniform Bound

![Similar Hypotheses](E:\学习笔记\mkdocs\MachineLearning\docs\Foundations\resources\imgs\Lecture 5 Training versus Testing\similar_hypotheses.png)
<br/>
$$
B_{m} : | E_{\text { in }}\left(h_{m}\right)-E_{\text { out }}\left(h_{m}\right) |>\epsilon
$$

for most $D$,$E_{\mathrm{in}}(h_i) = E_{\mathrm{in}}(h_j)$
$E_{\mathrm{out}}(h_i) \approx E_{\mathrm{out}}(h_j)$

$\begin{aligned}\mathbb{P}_{\mathcal{D}}[\mathrm{BAD} \ \mathcal{D} \ for \ h_1]+\mathbb{P}_{\mathcal{D}}[\mathrm{BAD} \ \mathcal{D} \ for \ h_2]+...+\mathbb{P}_{\mathcal{D}}[\mathrm{BAD} \ \mathcal{D} \ for \ h_M](union \ bound)\end{aligned}$ **over-estimating**

为了合并重叠的部分，我们按照类别将类似的假设分组归类。

<br/>

### Many Lines
$$
\mathcal{H}=\left\{\text { all lines in } \mathbb{R}^{2}\right\}
$$

<br/>

## Effective Number of Hypotheses

![1点2个类别](E:\学习笔记\mkdocs\MachineLearning\docs\Foundations\resources\imgs\Lecture 5 Training versus Testing\one_point_two_kinds.png)
**1点2个类别**
<br/>



![2个点4个类别](E:\学习笔记\mkdocs\MachineLearning\docs\Foundations\resources\imgs\Lecture 5 Training versus Testing\two_points_four_kinds.png)
**2个点4个类别**
<br/>

![3个点6个类别](E:\学习笔记\mkdocs\MachineLearning\docs\Foundations\resources\imgs\Lecture 5 Training versus Testing\three_points_six_kinds.png)

**3个点6个类别**
<br/>

![4个点14个类别](E:\学习笔记\mkdocs\MachineLearning\docs\Foundations\resources\imgs\Lecture 5 Training versus Testing\four_points_fourteen_kinds.png)

**4个点14个类别**
<br/>

$effective(N)<< 2^N$,用有效类别数($effective(N)$)替换$M$(infite)
<br/>

### Fun Time
What is the effective number of lines for five inputs $  \in R^2$ ?
1.&nbsp; 14 &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp; 2.&nbsp;16 &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;3.&nbsp;**22**&nbsp;$\checkmark$&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp; 4.&nbsp;32
<br/>
**Explanation**
总共有32($2^5$)种
5个O:1种，4个O1个X:5种，3个O2个X:共有$C_5^3$10种，只有5种满足条件。
而又O和X等价
所以有效类别数共有2X(1+5+5)=22种。

<br/>


### Growth Function
$effective(N)<< 2^N$
$M \Rightarrow effective(N)$
<br/>

**Growth Function for Positive Rays**

![Positive Rays](E:\学习笔记\mkdocs\MachineLearning\docs\Foundations\resources\imgs\Lecture 5 Training versus Testing\positive_rays.png)
$$
h(x)=\operatorname{sign}(x-a)
\\ m_{\mathcal{H}}(N)=N+1 \ll 2^{N}
$$
<br/>

**Growth Function for Positive Intervals**

![Positive Intervals](E:\学习笔记\mkdocs\MachineLearning\docs\Foundations\resources\imgs\Lecture 5 Training versus Testing\positive_intervals.png)
$$
h(x)=+1 \text { if } x \in[\ell, r),-1 \ otherwise
\\ m_{\mathcal{H}}(N)=\frac{1}{2} N^{2}+\frac{1}{2} N+1 \ll 2^{N}
$$
<br/>

**Growth Function for Convex Sets**

![Convex Sets](E:\学习笔记\mkdocs\MachineLearning\docs\Foundations\resources\imgs\Lecture 5 Training versus Testing\convex_sets.png)
$$
every \ dichotomy \ can \ be \ implemented
\\ m_{\mathcal{H}}(N)=2^{N}
$$

$m_{\mathcal{H}}(N)=2^{N}$ call those $N$ inputs ‘shattered’ by $H$
<br/>

### Fun Time
Consider **positive and negative rays** as H, which is equivalent to **the perceptron hypothesis set in 1D**. The hypothesis set is often called ‘decision stump’ to describe the shape of its hypotheses. What is the growth function $m_H (N)$?
1.&nbsp; N&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp; 2.&nbsp;N+1 &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;3.&nbsp;**2N**&nbsp;$\checkmark$&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp; 4.&nbsp;$2^N$
<br/>
**Explanation**
正或负方向的Positive Intervals，再加上全X和全O。
2X(N-1)+2 = 2N
<br/>

## Break Point
$m_{\mathcal{H}}$是多项式($O\left(N^{k-1}\right)$)，我们用它替换$M$

$m_{\mathcal{H}}(k)<2^{k}$ call k a break point for $H$ 

if k is a break point, k+1, k+2, k+3,... also break points!  k is the  **minimum break point**.

![The Four Break Points](E:\学习笔记\mkdocs\MachineLearning\docs\Foundations\resources\imgs\Lecture 5 Training versus Testing\four_break_points.png)
<br/>

### Fun Time
Consider **positive and negative rays** as H, which is equivalent to **the perceptron hypothesis set in 1D**. As discussed in an earlier quiz question, the growth function $m_H (N) = 2N$. What is the minimum break point for $H$?
1.&nbsp; 1&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp; 2.&nbsp;2&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;3.&nbsp;**3**&nbsp;$\checkmark$&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp; 4.&nbsp;4
<br/>
**Explanation**
$$
m_H (N) = 2N
\\ 2*2 = 4 = 2^2, \quad 2*3 = 6 < 2^3
$$
正负线的"一线曙光"是3.
<br/>




## Summary
<br/>

### 讲义总结
$m_{\mathcal{H}}$是多项式($O\left(N^{k-1}\right)$)，我们用它替换$M$，降低假设集的上界。
<br/>

**Recap and Preview**
&emsp;&emsp;two questions: $E_{out} (g) ≈ E_{in} (g)$, and $E_{in} (g) ≈ 0$
<br/>

**Effective Number of Lines**
&emsp;&emsp;at most 14 through the eye of 4 inputs
<br/>

**Effective Number of Hypotheses**
&emsp;&emsp;at most $m_H (N)$ through the eye of $N$ inputs
<br/>

**Break Point**
&emsp;&emsp;when $m_H (N)$ becomes ‘non-exponential’

<br/>

### 参考文献
<a href="https://www.csie.ntu.edu.tw/~htlin/course/mlfound18fall/">《Machine Learning Foundations》(机器学习基石)—— Hsuan-Tien Lin (林轩田)</a>