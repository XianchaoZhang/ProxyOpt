<!--
# ProxyOpt
Unofficial implement of denoising SIDD dataset reference the article Hyperparameter Optimization in Black-box Image Processing using Differentiable Proxies
 -->
# ProxyOpt
去噪 SIDD 数据集的非官方实现参考文章 Hyperparameter Optimization in Black-box Image Treatment using Differentiable Proxies

<!--
We use 10 instances of SIDD dataset that meet the conditions in the paper. Each instances we crop 300 512x512 image pair (noisy and gt).
 -->
我们使用满足论文中条件的 SIDD 数据集的 10 个实例。每个实例我们裁剪 300 个 512x512 图像对（有噪点和 gt）。

<!--
### step1
The first step is to train a net to fit the function of bm3d noise reduction. Inputs are noisy images cat with parameter layers, labels are the images dealed by bm3d.
 -->
### step1 
第一步是训练一个网络来拟合bm3d降噪的函数。输入是带有参数层的噪声图像 cat，标签是 bm3d 处理的图像。

<!--
### step2
The second step is to find the optimal bm3d parameters suitable for this dataset. We fixed the net parameter and update the parameter layer which cat input noisy images. Inputs are noisy images cat with random initialize parameter layer, labels are ground truth images.
 -->
### step2
第二步是找到适合该数据集的最佳 bm3d 参数。我们修复了网络参数并更新了输入噪声图像的参数层。输入是具有随机初始化参数层的噪声图像猫，标签是地面实况图像。


<p align="center">
  <img src="https://github.com/Apathetically/ProxyOpt/blob/master/results/readme/figure_1.png" width="400"/>
  <img src="https://github.com/Apathetically/ProxyOpt/blob/master/results/readme/figure_2.png" width="400"/>
</p>


<!--
### loss of step1
 -->
### 步骤 1 的 loss


<p align="center">
  <img src="https://github.com/Apathetically/ProxyOpt/blob/master/results/readme/train_step1.png" width="625"/>
</p>

<!--
However, we find that the net after step1 can not simulate the situation of poor parameter initialization. It will improve images with poor noise reduction due to poor initialization, as shown in the fourth row.
 -->
然而，我们发现step1之后的网络无法模拟参数初始化不佳的情况。它将改善由于初始化不良而降噪效果不佳的图像，如第四行所示。

<!--
Because of this, it may be difficult to optimize the parameters in step2.
 -->
因此，可能很难优化步骤2中的参数。


<p align="center">
  <img src="https://github.com/Apathetically/ProxyOpt/blob/master/results/readme/psnr.png" width="320"/>
  <img src="https://github.com/Apathetically/ProxyOpt/blob/master/results/readme/262.png" width="425"/>
</p>

<!--
### optimize parameter in step2
 -->
### 优化步骤2中的参数

<!--
Temporarily vacant
 -->
暂时空缺

<!--
### results
 -->
### 结果

<!--
Here we give the results of network simulation. Following image depict the psnr after step1 and step2. And more results given behind. The final psnr is about 34.71 for step1 and 34.75.
 -->
这里我们给出网络仿真的结果。下图描绘了步骤 1 和步骤 2 之后的 psnr。后面给出了更多的结果。步骤 1 和 34.75 的最终 psnr 约为 34.71。

<!--
note: top left [gt], top right [noisy], bottom left [bm3d], bottom right [net].
 -->
注意：左上[gt]、右上[noisy]、左下[bm3d]、右下[net]。


<p align="center">
  <img src="https://github.com/Apathetically/ProxyOpt/blob/master/results/readme/figure_5.png" width="400"/>
  <img src="https://github.com/Apathetically/ProxyOpt/blob/master/results/readme/182.png" width="400"/>
  <img src="https://github.com/Apathetically/ProxyOpt/blob/master/results/readme/24.png" width="400"/>
  <img src="https://github.com/Apathetically/ProxyOpt/blob/master/results/readme/84.png" width="400"/>
</p>


<!--
### apply optimized parameter into bm3d
 -->
### 将优化参数应用到 bm3d 中

<!--
We optimize parameter layer several times and does not optimize the same parameters. We use one to bm3d and it can improve psnr from 35.+ to 37.+.
 -->
我们多次优化参数层，不会优化相同的参数。我们使用 1 到 bm3d，它可以将 psnr 从 35.+ 提高到 37.+。


