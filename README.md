# -Chinese-text-sentiment-analysis-
# 中文文本情感分类

## 简介：

本实例对开源中文文本分类数据集，利用LSTM模型实现情感分类。类别共三种：好评、中性评论、差评。训练框架为TensorFlow2.4.1

训练最终准确率：
__训练集:0.97,测试集：0.86__

模型训练流程为：

（1）导入语言模型

选择开源中文训练模型：[wiki语言模型](https://github.com/Embedding/Chinese-Word-Vectors)
该开源语言模型库有多种预料训练的模型，本实例选择由wiki语料训练的语言模型。该语言模型的词向量长度为300，词种类30000+。本实例为了提高训练速度，只选取前10000组词。
（词id的查找随着语料库的增大，花费的时间也增大。正常情况下，词频在前10000的词语基本覆盖生活中常见的词语）
    
语言模型的词语需要和对应的词向量分离，并且基于有序的编号。后续按照词语查找编号，根据编号查找词向量。

（2）训练集与测试集处理
    
数据集来源：[网络开源数据集] (https://www.bilibili.com/video/BV1NJ411o7u3)
数据集下载之后需要进行前处理，包括对样本和标签的分离；样本（每条评论）的分词；

（3）统计所有评论的平均长度（每句话分词之后，每句话含有的词语个数）
    
得到平均长度之和，长于该长度的截断，低于改长度的补零。
    
（4）word2id

找到每个词语的id
    
（5）训练集和测试集数据准备

将每个id链接到对应的词向量，组成训练矩阵[训练集样本数，评论平均长度，词向量维度]与测试集。
    
（6）初始化LSTM模型参数

（7）构建模型

（8）模型训练

（9）模型测试


__待完成工作__
（1）模型明显存在过拟合现象，需要修改一些超参数继续训练；
（2）更换模型，从单向LSTM更换为双向BiLSM，观察训练效果；
（3）增加句子词语的平均长度。
