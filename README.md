# NLP_learning
* 记录自己学习NLP与tensorflow的过程。

* NLP常见算法实现主要参考[brightmart/text_classification](https://github.com/brightmart/text_classification)，代码和注释都非常清晰。
* 数据来源：2017知乎看山杯 <https://biendata.com/competition/zhihu/>

### 博客笔记

专栏：[NLP与tensorFlow学习](https://blog.csdn.net/qq_36153312/column/info/34223)

[记录TensorFlow学习中的参考文档](https://blog.csdn.net/qq_36153312/article/details/87896720)

[FastText模型原理](https://blog.csdn.net/qq_36153312/article/details/87897054)

[TextCNN模型原理](https://blog.csdn.net/qq_36153312/article/details/87936886)

[RNN与LSTM模型原理](https://blog.csdn.net/qq_36153312/article/details/88698410)

[Seq2Seq -- Attention -- Transformer](https://blog.csdn.net/qq_36153312/article/details/88770856)

### 模型实现笔记

[FastText模型](https://blog.csdn.net/qq_36153312/article/details/87897054)：[Bag of Tricks for Efficient Text Classification](https://arxiv.org/abs/1607.01759)

代码模块：超参数设置 -- 设置输入 -- 参数初始化 -- inference -- 设置loss节点train_op

**其中，inference包括embedding -- 线性分类器**

* **单标签**
  * 只使用预训练的char embedding和title char、desc char，假设每个问题只有一个标签，共1999个
  * FastText/pre_processing.ipynb对数据进行预处理
  * FastText/FastText.ipynb实现模型，并进行训练，在验证集上准确率最高为0.270（embedding可变），若固定embedding，最高为0.148
  * 使用softmax作为损失函数，准确率最高为0.30
* **多标签**
  * 只使用预训练的char embedding和title char、desc char，每个问题有至多5个标签
  * FastText/pre_processing_multilabel.ipynb对数据进行预处理，或直接使用上述github中提供的处理好的数据



[TextCNN模型](https://blog.csdn.net/qq_36153312/article/details/87936886)：[Convolutional Neural Networks for Sentence Classification](http://www.aclweb.org/anthology/D14-1181)

代码模块：超参数设置 -- 设置输入 -- 参数初始化 -- inference -- 设置loss节点train_op

**其中，inference包括embedding -- 卷积[conv2d - BN - ReLU - max_pooling - dropout - dense] -- 线性分类器**

* **单标签**
  * 只使用预训练的char embedding和title char、desc char，假设每个问题只有一个标签，共1999个
  * 仍使用FastText/pre_processing.ipynb对数据进行预处理，即数据与FastText相同
  * 准确率约为0.20
* **多标签**
  - 只使用预训练的char embedding和title char、desc char，每个问题有至多5个标签
  - FastText/pre_processing_multilabel.ipynb对数据进行预处理，或直接使用上述github中提供的处理好的数据
  - F1 score最高为0.31



[TextRNN模型](https://blog.csdn.net/qq_36153312/article/details/88698410)

代码模块：超参数设置 -- 设置输入 -- 参数初始化 -- inference -- 设置loss节点train_op

**其中，inference包括embedding -- 双向LSTM -- concat -- 线性分类器**

- **单标签**
  - 只使用预训练的char embedding和title char、desc char，假设每个问题只有一个标签，共1999个
  - 仍使用FastText/pre_processing.ipynb对数据进行预处理，即数据与FastText相同
  - 随机初始化embedding时准确率约为0.281，使用embedding（trainable）准确率约为0.294
- **多标签**
  - 只使用预训练的char embedding和title char、desc char，每个问题有至多5个标签
  - FastText/pre_processing_multilabel.ipynb对数据进行预处理，或直接使用上述github中提供的处理好的数据
  - F1 score最高为0.301



### Reference

[1] [brightmart/text_classification](https://github.com/brightmart/text_classification)

[2] [Bag of Tricks for Efficient Text Classification](https://arxiv.org/abs/1607.01759)

[3] [Convolutional Neural Networks for Sentence Classification](http://www.aclweb.org/anthology/D14-1181)

[4] [RNN](https://blog.csdn.net/zhaojc1995/article/details/80572098)

[5] 《百面机器学习》