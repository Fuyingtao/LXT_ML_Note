## 机器学习的流程
data(observation)->ML->skill(performance improving)

## 机器学习的三个主要因素（判断是否可以使用机器学习的方法）
1）存在一些潜在的模式或规律可以被学习到  
2）问题解决很难去程序化定义（比如定义一棵树）
3）有数据可以利用

## 启发
### 关于实际问题解决
关于机器学习应用的教学系统的设计一例，使用ML预测学生是否可以答出某个问题。其思路是先确定一个判断准则，然后让机器学习去学习该准则中的两个构成要素，可能这里面涉及到预测变量的转化问题。也就是说一个问题的解决可以转化为不同的问题解决阶段，而不是盲目地把最终问题当做机器学习的最终问题，机器学习可以应用在问题解决的任意阶段，其他阶段或者可以利用显示编程的方法实现。

### 机器学习的定义

f(unknown target function) -> Data -> H(hypothesis set)+A(learning algorithm) -> hypothesis g

机器学习模型指的是假设空间和学习算法两部分，初步理解学习算法指的是梯度下降法、牛顿法、坐标上升法这一类，不清楚cost function属于哪部分。

