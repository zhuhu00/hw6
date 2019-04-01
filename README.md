# 数字图像处理第六次作业
## 朱虎 自动化66 2161800226

提交日期：2019年3月31日  
## 摘要
本次报告主要记录了第六次作业中各项任务完成情况。本次作业以MATLAB2018a为平台，结合matlab本身有的函数对图像文件进行相关处理。1.在测试图像上产生高斯噪声，并且可以指定均值和方差。通过matlab本身的`imnoise()`函数可以添加，另外，本次作业中通过利用 `randn()` 函数来写了一个可以自己指定均值和方差的函数。通过比较可以发现该函数所实现的效果与matlab自带的函数差别很小。2. 在测试图像上加入密度均为0.1的椒盐噪声，该噪声也可以通过`imnoise()`来实现，此外，还写了可以自己指定密度的椒盐噪声函数`jiaoyan()`。3. 实现下面要求：a.实现模糊滤波器如方程Eq.(5.6-11);b. 模糊lena图像，并达到了对应的效果，c. 在模糊lena图像中增加高斯噪声，均值为0，方差为10pixels以产生退化图像；(d)分别利用方程Eq.(5.8-6)和(5.9-4)，恢复图像，也得到了预期的结果。
## 实验原理、过程、结果分析讨论
作业要求：  
1. 在测试图像上产生高斯噪声lena图-需能指定均值和方差；并用多种滤波器恢复图像，分析各自优缺点；  
2. 在测试图像lena图加入椒盐噪声（椒和盐噪声密度均是0.1）；用学过的滤波器恢复图像；在使用反谐波分析Q大于0和小于0的作用；  
3. 推导维纳滤波器并实现下边要求；  
(a) 实现模糊滤波器如方程Eq. (5.6-11).  
(b) 模糊lena图像：45度方向，T=1；   
(c) 再模糊的lena图像中增加高斯噪声，均值= 0 ，方差=10 pixels 以产生模糊图像；  
(d) 分别利用方程 Eq. (5.8-6)和(5.9-4)，恢复图像；并分析算法的优缺点.   

### 1. 在测试图像上产生高斯噪声lena图-需能指定均值和方差；并用多种滤波器恢复图像，分析各自优缺点
- **问题分析**
对给出的测试图，添加高斯噪声并用多种滤波器恢复图像。matlab自带的函数中，有`imnoise()` 函数可以直接添加噪声，也可以利用`randn()`来帮助生成一个噪声图片，由该噪声与源图像之和，即为添加噪声后的图像。  
图像恢复的原理事建立在图像退化的数学模型基础上的，通过研究模型，可以知道图像退化的原因。图像退化过程可以理解为施加于源图像上的运算和噪声两者的联合作用。  
而利用多种滤波器来恢复的原理多为前几次作业中实现的滤波器，这里就不再赘述原理。
- **处理结果**
加入高斯噪声的结果  
![1](https://github.com/zhuhu00/hw6/tree/master/pic/p_g.jpg)  
通过各种滤波恢复后的图像如下：  
![2](https://github.com/zhuhu00/hw6/tree/master/pic/p11_z.jpg)    
![2](https://github.com/zhuhu00/hw6/tree/master/pic/p12.jpg)   
![2](https://github.com/zhuhu00/hw6/tree/master/pic/p13.jpg)   
![2](https://github.com/zhuhu00/hw6/tree/master/pic/p15.jpg)   

- **结果分析**
通过自己设计的高斯噪声可以知道，高斯噪声污染到的图像，当高斯噪声的均值不变，为0时，随着方差的增加，图像噪声越来越严重；当高斯噪声方差不变时，均值会影响到整个图像的灰度值，使整个图像变亮。从理论上均值和方差对图像的影响一致。分别使用高斯滤波器和中值滤波器对加噪图像进行恢复。这些方法都能在一定程度上降低噪声。

### 2. 在测试图像lena图加入椒盐噪声（椒和盐噪声密度均是0.1）；用学过的滤波器恢复图像；在使用反谐波分析Q大于0和小于0的作用
- **问题分析** 
添加椒盐噪声，并且密度为0.1，可以使用matlab自带函数`imnoise()`来生成噪声，也可以使用自己写的函数`jiaoyan()`来生成噪声，其原理主要是通过需要生成两种噪声，则在生成的噪声密度选择上直接影响到效果。通过两种密度，分别生成逻辑矩阵（矩阵中只含有0，1），然后两个矩阵相与之后的图像即为添加后的图像。之后利用前述叙述的滤波器进行滤波，这里还有一种更适合去除椒盐噪声的滤波器是逆谐波均值滤波器。通过设置Q的大小，可以选择是否适合去除该种噪声。通过分析对比，得到结论。
- **实验结果**
添加椒盐噪声后的图像如下所示    
![](https://github.com/zhuhu00/hw6/tree/master/pic/p_j.jpg)  
进行滤波后的图像为  
![](https://github.com/zhuhu00/hw6/tree/master/pic/p21.jpg)  
![](https://github.com/zhuhu00/hw6/tree/master/pic/p23.jpg)  
![](https://github.com/zhuhu00/hw6/tree/master/pic/p25.jpg)    
使用逆谐波均值滤波器进行滤波结果  
分别添加胡椒和白盐噪声
![](https://github.com/zhuhu00/hw6/tree/master/pic/p2_j_y.jpg)
对加入胡椒噪声的图像进行逆谐波滤波如下（Q = 1.5或-1.5）   
![](https://github.com/zhuhu00/hw6/tree/master/pic/p2_h_nxb.jpg)     
对加入白盐噪声的图像进行逆谐波滤波如下（Q = 1.5或-1.5）    
![](https://github.com/zhuhu00/hw6/tree/master/pic/p2_h_nxb.jpg)   
 
- **结果分析**
在逆谐波滤波器种，Q的取值直接影响到直接能够去除的波形。通过比较可知，Q>0时，去除的是胡椒噪声，Q<0时适合用来去除白盐噪声。其原理如下所示：  
![1](https://github.com/zhuhu00/hw6/tree/master/gs/p1.jpg)   
从上式可以看出，其为求(x,y)领域内所有点的加权平均值，权重的分母为一个常数，因此我们只需要考虑分子的大小  
1. 当Q>0时，g(s,t)^Q有增强作用，由于胡椒噪声值比较小（0），因此滤波后噪点处的取值和周围其他值更接近，有利于消除呼叫噪声。  
2. 当Q<0时，g(s,t)^Q有增强作用，由于胡椒噪声值比较大(255),因此取倒数后比较小，对加权平均结果影响较小，所以滤波后噪点处(x,y)取值和其他点更接近，所以有利于消除白盐噪声。  

### 3. 推导维纳滤波器并实现下边要求；   
(a) 实现模糊滤波器如方程Eq. (5.6-11).    
(b) 模糊lena图像：45度方向，T=1；      
(c) 再模糊的lena图像中增加高斯噪声，均值= 0 ，方差=10 pixels 以产生模糊图像；    
(d) 分别利用方程 Eq. (5.8-6)和(5.9-4)，恢复图像；并分析算法的优缺点.   

- **问题分析**
1. 实现模糊滤波器如方程Eq.(5.6-11).
模糊滤波器频域表达式为：
![2](https://github.com/zhuhu00/hw6/tree/master/gs/p2.jpg)   
![3](https://github.com/zhuhu00/hw6/tree/master/gs/p3.jpg)   
![4](https://github.com/zhuhu00/hw6/tree/master/gs/p4.jpg)   
![5](https://github.com/zhuhu00/hw6/tree/master/gs/p5.jpg)   
![6](https://github.com/zhuhu00/hw6/tree/master/gs/p6.jpg)   
![7](https://github.com/zhuhu00/hw6/tree/master/gs/p7.jpg)   
$$
\mathbf{V}_1 \times \mathbf{V}_2 =  \begin{vmatrix} 
\mathbf{i} & \mathbf{j} & \mathbf{k} \\
\frac{\partial X}{\partial u} &  \frac{\partial Y}{\partial u} & 0 \\
\frac{\partial X}{\partial v} &  \frac{\partial Y}{\partial v} & 0 \\
\end{vmatrix}
$$tep1}{\style{visibility:hidden}{(x+1)(x+1)}}
$$  
- **实验结果**
1. 实现模糊滤波器  
其频域表达式为：  
![8](https://github.com/zhuhu00/hw6/tree/master/gs/p8.jpg)  
故实现该滤波器需要将图像进行傅里叶变换后并移至图像中心，之后将图像的傅里叶变换和模糊滤波器的傅里叶变换进行阵列相乘，将得到的结果经过傅里叶反变换返回到空间域即可实现滤波器。
2. 模糊lena图像：45度方向，T=1； 
3. 在模糊后的图像中加入高斯噪声（均值为0；方差为0.01) 
![](https://github.com/zhuhu00/hw6/tree/master/pic/p31.jpg)   
4. 分别利用方程 Eq. (5.8-6)和(5.9-4)，恢复图像。
维纳滤波结果：  
![](https://github.com/zhuhu00/hw6/tree/master/pic/p3_mh_w.jpg)  
约束最小二乘法滤波的结果：
![](https://github.com/zhuhu00/hw6/tree/master/pic/p3_y_l.jpg)   

- **结果分析和总结**
通过自己编写的模糊函数对图像进行处理，结合MATLAB中的`imfilter()`和`fspecial()`函数，对图像进行了模糊滤波，模糊的效果基本是一致的。之后调用`imnoise()`进行添加了高斯噪声，得到模糊并加上高斯噪声的结果。  
之后利用matlab提供的`deconvwnr()`函数进行维纳滤波，运动模糊的影响基本被消除，但是噪声的影响依旧较大，导致图像质量下降；  
之后利用了matlab中的`deconvreg()`函数进行了约束最小乘方滤波。从滤波后的结果看，约束最小二乘法滤波得到了比维纳滤波更好地结果，尤其是对噪声的滤除。  


> [1]冈萨雷斯.数字图像处理(第三版)北京:电子工业出版社,2011   
> [2]周品.MATLAB数字图像处理北京:清华大学出版社,2012