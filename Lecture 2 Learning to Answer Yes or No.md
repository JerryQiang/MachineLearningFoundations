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
PLA算法就是要在Perceptrons(Perceptron Hypothesis Set)找到合适的Perceptron，而Perceptron由$w$决定，即找到合适$w$，使样本完全分开。
### Cyclic PLA
Cyclic PLA算法如下所示
（1）初始化$w​$->$w_0​$
（2）更新$w​$
&emsp;&emsp;For t = 0,1,...
&emsp;&emsp;&emsp;&emsp;find a mistake of $w_t​$ called ($x_{n(t)}​$,$y_{n(t)}​$)
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;$sign(w_t^Tx_{n(t)}) \ne y_{n(t)}​$

&emsp;&emsp;&emsp;&emsp;correct the mistake by
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;$w_{(t+1)} ← w_t + y_{n(t)}x_{n(t)}​$

&emsp;&emsp;... until no more mistakes
&emsp;&emsp;return last w (called w PLA ) as g	

PLA算法的精髓在于**找到与感知器分类不正确的点，然后通过不正确的点修正感知器，直到所有的样本点分类正确。**
修正公式：$w_{(t+1)} ← w_t + y_{n(t)}x_{n(t)}$
修正图示：
![1555492432358](E:\学习笔记\mkdocs\MachineLearning\docs\Foundations\resources\imgs\Lecture 2 Learning to Answer Yes or No\PLA_update_w.png)
<br/>

### Fun Time
**Let’s try to think about why PLA may work.**
**Let n = n(t), according to the rule of PLA below, which formula is true?**
$$
sign(w_t^Tx_{n}) \ne y_{n}，\quad
w_{(t+1)} ← w_t + y_{n}x_{n}
$$
1.&nbsp;$w_{t+1}^Tx_{n} =  y_{n}$
2.&nbsp;$sign(w_{t+1}^Tx_{n}) = y_{n}$
3.&nbsp;$y_{n}w_{t+1}^Tx_{n} \geq y_{n}w_{t}^Tx_{n}$ &nbsp;$\checkmark$
4.&nbsp;$y_{n}w_{t+1}^Tx_{n} < y_{n}w_{t}^Tx_{n}​$

**Explanation**
经过($x_{n}$, $y_{n}$)更新后，$w_t$到$w_{t+1}$的变化
由于感知器是相对修正($\Delta w = y_{n}x_{n}$)，修正后不一定就能将($x_{n}$, $y_{n}​$)分类正确。

$$
y_{n}w_{t+1}^Tx_{n} - y_{n}w_{t}^Tx_{n} =  (w_{t+1}^T-w_{t}^T)y_{n}x_{n} = x_{n}^Ty_{n}^Ty_{n}x_{n} 
\stackrel{y_{n}^Ty_{n}= +1}{\xlongequal{\quad\quad\quad}} x_{n}^Tx_{n} \ge 0​
$$

<br/>



## Guarantee of PLA
<br/>

### Linear Separability
if **PLA halts** (i.e. no more mistakes), (necessary condition) D allows **some w** to **make no mistake** call such **D linear separable.**

linear separable $D​$ ⇔ exists **perfect** $\mathbf{w_f}​$ such that $sign(w_f^Tx_{n}) = y_{n}​$

Fun Time中我们推导出感知器每次修正，$y_{n}w_{t+1}^Tx_{n} \ge y_{n}w_{t}^Tx_{n}$, $w_t$就会向$w_f$逼近。
我们计算$\Delta w_f^Tw_{t+1}​$再次确认下
$$
\because w_f \ is \ perfect \ for \ x_n
\\ \therefore y_{n(t)}w_t^Tx_{n(t)} \ge \mathop{min}\limits_n \, y_{n(t)}w_t^Tx_{n(t)} > 0
\\
\mathbf{w_t^Tw_{n(t)} \uparrow} \ by \ updating \ with \ any \ (x_{n(t)}, y_{n(t)})
\\
\begin{equation}
\begin{aligned} 
\mathbf{w}_{f}^{T} \mathbf{w}_{t+1} &= \mathbf{w}_{f}^{T}\left(\mathbf{w}_{t}+y_{n(t)} \mathbf{x}_{n(t)}\right) \\ & \geq \mathbf{w}_{f}^{T} \mathbf{w}_{t}+\min _{n} y_{n} \mathbf{w}_{f}^{T} \mathbf{x}_{n} \\ &>\mathbf{w}_{f}^{T} \mathbf{w}_{t}+0 
\end{aligned}
\end{equation}
$$

感知器每次修正，$\mathbf{w}_{f}^{T} \mathbf{w}_{t+1} > \mathbf{w}_{f}^{T} \mathbf{w}_{t}$，$w_t$是在向$w_f$逼近。

但是我们希望的逼近是夹角的逼近，而不是数值的增大。计算$\Delta||w_t||^2​$。




## Non-Separable Data
	hold somewhat ‘best’ weights in pocket

## Summary
### 讲座总结
Perceptron Hypothesis Set
	hyperplanes/linear classifiers in $R_d​$
Perceptron Learning Algorithm (PLA)
​	correct mistakes and improve iteratively
Guarantee of PLA
	no mistake eventually if linear separable
Non-Separable Data
	hold somewhat ‘best’ weights in pocket