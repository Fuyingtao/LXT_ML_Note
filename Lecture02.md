# 感知机算法（Perceptron Learning Algrithm, PLA）
## 感知机算法的Hypothesis
$$
\begin{align}
h(x) & = \text{sign}(\sum_{i=0}^Nw_{i}x_{i}),\quad  x_0=1 \\\\
     & = \text{sign}(w^{T}x)
\end{align}
$$
实际上得到的判断标准是直线或超平面$\text{sign}(\sum_{i=0}^{N}w_{i}x_{i}) = 0$,所以PLA是线性分类器。
*H表示成向量相乘的形式，其正负即表示向量之间的夹角，利用此视角进行后续寻找算法的实现*

## 感知机算法的实现：从假设空间中寻找$g \approx f$
首先初始化一条线$w_{0}$.然后找到一个错误数据点，对$w_{0}$进行校正。校正原则就是根据向量相乘的原理，根据向量相乘的正负判断其夹角，然后根据向量加减对向量乘积进行校正。总结其校正原则就是$w_{t+1} = w_{t}+y_{n}x_{n}$, $y_{n}x_{n}$就是$w_{t}$判断错误的那个点。

一直做到循环一圈0错误为止（此时假设数据是线性可分的）。

## 在数据线性可分的条件下，证明PLA的收敛性
假设存在$w_{f}$使得任意$y_{n}=sign(w_{f}^Tx_{n})$, 即数据线性可分， 
起始点设$w_{0}=0$,
经过$T$次错误修正以后，$w_{T}$与$w_{f}$的夹角余弦值可以表示为
$$\frac{w_{f}^{T}}{\lVert w_{f}\rVert}\frac{w^{T}}{\lVert w_{T}\rVert}$$
其中，
$$
\begin{align}
w_{f}^{T}w_{T} & = w_{f}^{T}(w_{0} + \sum_{t=1}^{T}y_{n(t)}x_{n(t)})  \\\\
                 & = w_{f}^{T}\sum_{t=1}^{T}y_{n(t)}x_{n(t)} \\\\
                 & = \sum_{t=1}^{T}y_{n(t)}w_{f}^{T}x_{n(t)} \\\\
                 & \ge T\min_{n}y_{n}w_{f}^{T}x_n
\end{align}
$$
$$
\begin{align}
\lVert w_{T}\rVert^2 & = \lVert w_{T-1}+y_{n(T-1)}x_{n(T-1)}\rVert^2 \\\\
                 & = \lVert w_{T-1}\rVert^2 + \lVert y_{n(T-1)}x_{n(T-1)}\rVert^2 + 2y_{n(T-1)}w_{T-1}x_{n(T-1)} \\\\
                 & \le \lVert w_{T-1}\rVert^2 + \lVert y_{n(T-1)}x_{n(T-1)}\rVert^2 + 0 \\\\
                 & \le \lVert w_{0}\rVert^2 + \sum_{t=0}^{T-1}\lVert y_{n(t)}x_{n(t)}\rVert^2 \\\\
                 & \le T\max_{n}\lVert x_{n}\rVert^2
\end{align}
$$
即
$$
\begin{align}
\lVert w_{T}\rVert \le \sqrt{T}\max_{n}\lVert x_{n}\rVert
\end{align}
$$
综上
$$
\begin{align}
\frac{w_{f}^{T}}{\lVert w_{f}\rVert}\frac{w^{T}}{\lVert w_{T}\rVert} & \ge \frac{T\min_{n}y_{n}w_{f}^{T}x_n}{\lVert w_{f}\rVert \sqrt{T}\max_{n}\lVert x_{n}\rVert}\\\\
& =\sqrt{T}\frac{\min_{n}y_{n}w_{f}^{T}x_n}{\lVert w_{f}\rVert \max_{n}\lVert x_{n}\rVert}
\end{align}
$$
所以两者的夹角余弦值下限不断变大，最终可以到达最大值1。

## 数据线性不可分时怎么办
口袋算法（Pocket Algorithm）：每次选一条犯错误最少的线




