# NLP_learning
* 记录自己学习NLP与tensorflow的过程。

* NLP常见算法实现主要参考[brightmart/text_classification](https://github.com/brightmart/text_classification)，代码和注释都非常清晰。
* 数据来源：2017知乎看山杯 <https://biendata.com/competition/zhihu/>

### 博客笔记

专栏：[NLP与tensorFlow学习](https://blog.csdn.net/qq_36153312/column/info/34223)

[记录TensorFlow学习中的参考文档](https://blog.csdn.net/qq_36153312/article/details/87896720)

[FastText模型](https://blog.csdn.net/qq_36153312/article/details/87897054)：[Bag of Tricks for Efficient Text Classification](https://arxiv.org/abs/1607.01759)

代码模块：超参数设置 -- 参数初始化 -- inference -- 设置loss节点train_op

**其中，inference包括embedding -- 线性分类器**

* **单标签**
  * 只使用预训练的char embedding和title char、desc char，假设每个问题只有一个标签，共1999个
  * FastText/pre_processing.ipynb对数据进行预处理
  * FastText/FastText.ipynb实现模型，并进行训练，在验证集上准确率最高为0.270（embedding可变），若固定embedding，最高为0.148
* **多标签**
  * 只使用预训练的char embedding和title char、desc char，每个问题有至多5个标签
  * FastText/pre_processing_multilabel.ipynb对数据进行预处理，或直接使用上述github中提供的处理好的数据

[TextCNN模型](https://blog.csdn.net/qq_36153312/article/details/87936886)：[Convolutional Neural Networks for Sentence Classification](http://www.aclweb.org/anthology/D14-1181)

代码模块：超参数设置 -- 参数初始化 -- inference -- 设置loss节点train_op

其中，inference包括embedding -- 卷积[conv2d - BN - ReLU - max_pooling - dropout - dense] -- 线性分类器

### Reference

[1] [brightmart/text_classification](https://github.com/brightmart/text_classification)

[2] [Bag of Tricks for Efficient Text Classification](https://arxiv.org/abs/1607.01759)

[3] [Convolutional Neural Networks for Sentence Classification](http://www.aclweb.org/anthology/D14-1181)