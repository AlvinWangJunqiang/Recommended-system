# Recommended system



### als_mf算法流程：
- 初始化矩阵U和M，U矩阵大小为user_id * n_feature，其中user_id为用户id数，n_fearure为潜在特征；同理M矩阵大小为item_id * n_feature，其中item_id为项目id数；
- 生成user_id - item_id矩阵，其中行为user_id，列为item_id，值为用户评分rating，减去全局评分的均值；
- 误差等式为平方差公式，即真实值和预测值的评分差（R-U*M），为了防止过拟合，加上正则项，惩罚过大参数；
- 固定M矩阵，使用梯度下降，对误差等式f(U, M)求U梯度；
- 同样固定U矩阵，使用梯度下降，对误差等式f(U, M)求M梯度；
- 预测值为U*M，不断迭代上面两步，直到最近两次误差收敛到一个阈值时，停止更新参数（具体数学推导可看matrix factorization笔记及论文Large-scale Parallel Collaborative Filtering the Netflix Prize）

　　注意的是，进行参数更新的已评分的item_id和user_id的实例，即拟合已评分的user-item矩阵，然后去预测未评分的user-item的评分。 <br />
参考代码：https://github.com/chyikwei/recommend


### pmf算法流程：
　　pmf的算法流程与als_mf算法流程类似，除了最小化误差等式换为最小化能量函数，具体数学推导可看matrix factorization笔记及论文Probabilistic Matrix Factorization - NIPS Proceedings） <br />
参考代码：https://github.com/chyikwei/recommend

reference: <br />
http://www.quuxlabs.com/blog/2010/09/matrix-factorization-a-simple-tutorial-and-implementation-in-python/ <br />
http://blog.csdn.net/shenxiaolu1984/article/details/50372909 <br />
Probabilistic Matrix Factorization - NIPS Proceedings <br />
Large-scale Parallel Collaborative Filtering for the Netflix Prize <br />

### collaborative-filtering.py
　　来源：《集体智慧编程》第二章

### apriori算法流程：
- 支持度：support(A=>B)：A和B的同时出现的次数 / 总样本数
- 置信度：confidence(A=>B)：P(B | A) = support(A=>B) / support(A) <br />
参考代码：https://github.com/asaini/Apriori

#### factorization machines算法：
　　其思想是生成一个多项式，以二项式为例，即两两变量相乘，并乘以权重，这时使用矩阵分解技术，将二项式的权重矩阵拆分成两个矩阵，即 V x N = (V x k) \cdot (k x N)，一是能共享参数，二是能减少稀疏性。 <br >
资料主要参考美团这篇：https://tech.meituan.com/deep-understanding-of-ffm-principles-and-practices.html <br >
Factorization Machines: http://www.algo.uni-konstanz.de/members/rendle/pdf/Rendle2010FM.pdf

代码参考：<br >
https://github.com/princewen/tensorflow_practice/blob/master/recommendation/recommendation-FM-demo/FM_model.py  <br >
https://github.com/babakx/fm_tensorflow/blob/master/fm_tensorflow.ipynb <br >

### deepFM算法：
源代码参考：https://github.com/ChenglongChen/tensorflow-DeepFM



