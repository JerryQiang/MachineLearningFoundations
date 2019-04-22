[TOC]

# Lecture 7: The VC Dimension
<br/>

## Definition of VC Dimension
$m_{\mathcal{H}}(N)$ breaks at k(good $H$) and N large enough(good $D$) => $E_{\mathrm{out}} \approx E_{\mathrm{in}}$

$A$ picks a $g$ with small $E_{in}$ (good $A$) => $E_{\mathrm{in}} \approx 0$

最后学到了东西，到达了要求 => $E_{\mathrm{out}} \approx 0$

### VC Dimension
VC Dimension is the maximum of non-break point. 
&emsp;&emsp; largest N for which $m_H (N)$ = $2^N$
&emsp;&emsp; $d_{vc}$ =  ‘minimum k’ - 1 
&emsp;&emsp; the most inputs $H$ that can shatter
VC Dimension反映了假设集在数据集上的性质：数据集的最大分类情况。
$d_{vc}$和minimum break point都是"一线曙光"的分界点。
 $ if \ N \geq 2, d_{\mathrm{vc}} \geq 2, m_{\mathcal{H}}(N) \leq N^{d_{\mathrm{vc}}}$

![The Four VC Dimensions](E:\学习笔记\mkdocs\MachineLearning\docs\Foundations\resources\imgs\Lecture 7 The VC Dimension\four_vc_dimensions.png)

和之前一样(minimum break point finite)，我们希望$d_{vc}$ finite.

### Fun Time
If there is a set of $N$ inputs that cannot be shattered by $H$. Based only on this information, what can we conclude about $d_{VC} (H)$?
1 $d_{\mathrm{vc}}(\mathcal{H})>N$
2 $d_{\mathrm{vc}}(\mathcal{H})=N$
3 $d_{\mathrm{vc}}(\mathcal{H})<N$ 
4 **no conclusion can be made** &nbsp;$\checkmark$
<br/>
**Explanation**
这道题目当初也是百思不得其解，直到我又学习了一遍。
VC Dimension：the most inputs $H$ that can shatter
有N个数据no shatter不能代表其他的N个数据no shatter。
举例说明：
1维感知器 break point为3， 2维感知器 break point为4。
在2维空间中，连成一条直线的三个点（2维退化到1维），分类数只有6($<2^3$)种 。而2维感知器的break point却为4，这就是因为不在同一条直线上的三个点分类数可以为8。所以导致2维感知器的最小break point增大了。
这里面也蕴含着提升维度，增大了自由度。:-)

<br/>

## VC Dimension of Perceptrons
1D perceptron (pos/neg rays)：$d_{\mathrm{vc}}$ = 2
2D perceptrons: $d_{\mathrm{vc}}$ = 3
d-D perceptrons：$d_{\mathrm{vc}}= d + 1$ 
**证明分两步**:
&emsp;&emsp;• $d_{\mathrm{vc}}≥ d + 1$：存在(d+1)个点 shatter.
&emsp;&emsp;• $d_{\mathrm{vc}} ≤ d + 1$：任何(d+2)个点 no shatter.

### Extra Fun Time
What statement below shows that $d_{\mathrm{vc}}≥ d + 1$
1 **There are some d + 1 inputs we can shatter.** &nbsp;$\checkmark$
2 We can shatter any set of d + 1 inputs.
3 There are some d + 2 inputs we cannot shatter. 
4 We cannot shatter any set of d + 2 inputs.
<br/>
**Explanation**
存在(d+1)个点 shatter => $d_{\mathrm{vc}}≥ d + 1$
<br/>



![VC Dimension Step 1](E:\学习笔记\mkdocs\MachineLearning\docs\Foundations\resources\imgs\Lecture 7 The VC Dimension\vc_dimension_step1.png)

Special X（d+1个点） 对于任意的y，都有对应的hypothesis(w) .
<br/>

### Extra Fun Time

What statement below shows that $d_{\mathrm{vc}} \le d + 1$
1 There are some d + 1 inputs we can shatter. 
2 We can shatter any set of d + 1 inputs.
3 There are some d + 2 inputs we cannot shatter. 
4 **We cannot shatter any set of d + 2 inputs.** &nbsp;$\checkmark$
<br/>
**Explanation**
任何(d+2)个点 no shatter. => $d_{\mathrm{vc}} ≤ d + 1$
<br/>



![VC Dimension Step 2](E:\学习笔记\mkdocs\MachineLearning\docs\Foundations\resources\imgs\Lecture 7 The VC Dimension\vc_dimension_step2.png)

$x_{d+2}$与$x_1,x_2,...,x_{d+1}$线性相关，假设这任意d+2个点可以shatter，那么$a_1,a_2,...,a_{d+1},a_{d+2}$系数可以任意取，当$a_i=sign(w^Tx_i)$时，$w^Tx_d>0$，所以d+2个点no shatter.
<br/>

### Fun Time
Based on the proof above, what is d VC of 1126-D perceptrons?
1 1024
2 1126
3 **1127** &nbsp;$\checkmark$
4 6211
<br/>
**Explanation**
d-D perceptrons：$d_{\mathrm{vc}}= d + 1$ 
<br/>




## Physical Intuition of VC Dimension
$d_{\mathrm{vc}}(H)$:  powerfulness of $H$
$d_{\mathrm{vc}}$ ≈ #free parameters
$d_{\mathrm{vc}}$代表了**自由度**(与自由变量的个数相关)，我在学统计学时接触过自由度这个概念，若$\mu$（均值）确定，数据大小为N的自由度就为N-1，因为$\mu$确定，知道N-1个点，就能求出第N个点。
$d_{VC}(H)$就代表了$H$关于数据的自由度。
<br/>

### M and $d_{VC}$

![Choose the right H](E:\学习笔记\mkdocs\MachineLearning\docs\Foundations\resources\imgs\Lecture 7 The VC Dimension\d_vc.png)
<br/>
so choose the **right** $hypothesis \ set$($M$ or $d_{\mathrm{vc}}$).
<br/>

### Fun Time
Origin-crossing Hyperplanes are essentially perceptrons with $w_0$ fixed at 0. Make a guess about the$d_{\mathrm{vc}}$ of origin-crossing hyperplanes in $R_d$. 
1 1
2 **d** &nbsp;$\checkmark$
3 d+1
4 $\infty$
<br/>
**Explanation**
d-D perceptrons：$d_{\mathrm{vc}}= d + 1$
而穿过原点，加了一个限制条件，使自由度降1，故变成了d.
<br/>

## Interpreting VC Dimension
<br/>

### Penalty for Model Complexity
$$
\mathbb{P}_{\mathcal{D}}\left[\underbrace{\left[E_{\text { in }}(g)-E_{\text { out }}(g) |>\epsilon\right]}_{\text { BAD }}\right] \leq \underbrace{4(2 N)^{d_{vc}} \exp \left(-\frac{1}{8} \epsilon^{2} N\right)}_{\delta}
\\ probability ≥ 1 − \delta, \ \operatorname{GOOD} : | E_{in}(g)-E_{out}(g) | \leq \epsilon
\\ \delta=4(2 N)^{d_{\mathrm{vc}}} \exp \left(-\frac{1}{8} \epsilon^{2} N\right)
\\ \epsilon = \sqrt{\frac{8}{N} \ln \left(\frac{4(2 N)^{d_{\mathrm{vc}}}}{\delta}\right)}
\\ E_{out}(g) \leq E_{in}(g)+\sqrt{\frac{8}{N} \ln \left(\frac{4(2 N)^{d} v_{c}}{\delta}\right)}
$$


loosely: model complexity & sample complexity

## Summary
本篇讲义主要讲了loosely: model complexity & sample complexity。

<br/>

### 讲义总结

**Definition of VC Dimension**
&emsp;&emsp; maximum non-break point
<br/>

**VC Dimension of Perceptrons**
$d_{VC} (H)= d + 1$ 
<br/>

**Physical Intuition of VC Dimension**
$d_{VC}$ ≈ #free parameters
<br/>

**Interpreting VC Dimension**
<br/>

### 参考文献
<a href="https://www.csie.ntu.edu.tw/~htlin/course/mlfound18fall/">《Machine Learning Foundations》(机器学习基石)—— Hsuan-Tien Lin (林轩田)</a>