 pytorch-deep-learning
 ========
 优化算法
 -------
### 梯度下降与随机梯度下降
#### 一维梯度下降
  一维梯度下降可以让我们更加直观地去理解梯度下降的概念以及方式.优化算法的目标就是通过迭代不断更新变量值,使得目标函数f(x)的值不断减小,达到我们想要的效果.<br>
![一维梯度下降](https://github.com/MA-JIE/pytorch-deep-learning/blob/master/images/%E4%B8%80%E7%BB%B4.png)
![](https://github.com/MA-JIE/pytorch-deep-learning/blob/master/%E4%BC%98%E5%8C%96%E7%AE%97%E6%B3%95/images/1.png)

#### 多维梯度下降
  在神经网络中,我们处理的优化问题一般是多维的,需要同时去优化多维的变量,首先是去表示出目标函数对各个变量的偏导数. <br>
![](https://github.com/MA-JIE/pytorch-deep-learning/blob/master/images/2.png) <br>
  在某点x处,我们可以表示出以该点为圆心,半径为"1"的各个方向,向外散发的方向导数,然后我们期望得到使目标函数的值不断减小的同时,其减小的速度也是最快的,即寻找方向导数的最小值,这样是下降最快的方向. <br>
![](https://github.com/MA-JIE/pytorch-deep-learning/blob/master/%E4%BC%98%E5%8C%96%E7%AE%97%E6%B3%95/images/3.png)
![](https://github.com/MA-JIE/pytorch-deep-learning/blob/master/%E4%BC%98%E5%8C%96%E7%AE%97%E6%B3%95/images/4.png)

#### 随机梯度下降(SGD)
  在深度学习中,当我们构建好目标函数(通常训练数据集中有关各个样本的损失函数的平均)后,若采用梯度下降的方式,每次自变量的迭代更新需要不小的算力,但可以发现对某个样本的损失函数的随机梯度的期望就是整体目标函数的期望,由概率论中期望的公式很容易证得.<br>
  目标函数的定义为:<br>
  ![](https://github.com/MA-JIE/pytorch-deep-learning/blob/master/%E4%BC%98%E5%8C%96%E7%AE%97%E6%B3%95/images/5.png)<br>
  在X处的梯度为:<br>
  ![](https://github.com/MA-JIE/pytorch-deep-learning/blob/master/%E4%BC%98%E5%8C%96%E7%AE%97%E6%B3%95/images/6.png)<br>
  ![](https://github.com/MA-JIE/pytorch-deep-learning/blob/master/%E4%BC%98%E5%8C%96%E7%AE%97%E6%B3%95/images/7.png)<br>

#### 小批量随机梯度下降
  定义：在每次迭代中，随机均匀采样多个样本来组成一个小批量，然后使用这个小批量来计算梯度。<br>
 采样的方式包括：(1)重复采样. (2)不重复采样. 后者更为常见<br>
 ![](https://github.com/MA-JIE/pytorch-deep-learning/blob/master/%E4%BC%98%E5%8C%96%E7%AE%97%E6%B3%95/images/small_batch.png)<br>
 
#### 动量法
有时候使用随机梯度下降迭代自变量时，就二维举例，有可能在竖直方向比在水平方向移动幅度更大，因为竖直方向的梯度更大些。那么这个时候，我们希望用一个较小的学习率避免在竖直方向上越过目标函数最优解，然而，这样在水平方向移动会变慢。<br>
动量法是为了解决这样的问题。在动量法中，自变量在各个方向上的移动幅度不仅取决于当前梯度，还取决于过去的各个梯度在各个方向上是否一致。<br>
数学背景：<br>
![](https://github.com/MA-JIE/pytorch-deep-learning/blob/master/%E4%BC%98%E5%8C%96%E7%AE%97%E6%B3%95/images/exponentially_weighted_moving_average.png)
