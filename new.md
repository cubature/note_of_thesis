### 项目结构

```
<root>
│   emotic_keras_training.py
│   emotic_keras_glove.py
│   emotic_keras_test.py
│   tools.py
│   ...
└───data
│   │   generate_corpus.py
│   │   speech_to_text.py
│   │   <corpus>
│   └───models
│       │   output_graph.pbmm
│       │   alphabet.txt
│       │   ...
│   
└───glove
    │   glove.6B.100d.txt
```

根目录下为主要的训练及预测代码，其中`emotic_keras_training.py`、`emotic_keras_glove.py`为模型训练代码，`emotic_keras_test.py`为使用已训练模型的代码，`tools.py`包含一些工具函数。

在`data/`文件夹中放置原始数据集，然后通过`speech_to_text.py`进行语音转文字，通过`generate_corpus.py`进行数据集的预处理。`models/`文件夹中为一些DeepSpeech工具的模型。

`glove/`文件夹中的为预训练的GloVe模型。

### 环境及工具

* Windows
* Python > 3.4
* pip >= 19.0
* tensorflow 2.x
* keras 2.x

### 数据集预处理

#### 语音转文字工具DeepSpeech

由于没有找到非常合适的语音数据集，因此这一步不是必须的。

安装DeepSpeech库

```
pip3 install deepspeech
```

语音转文字

```
python3 speech_to_text.py --model ??? --?? ??? --?? ???
```

#### 生成训练集和测试集 (generate_corpus.py)

原始数据集的路径及生成数据集的路径名称通过修改文件中的？？？？？？实现。

运行文件：

```
python3 generate_corpus.py
```

生成两个文件，分别为训练集和测试集。

### 神经网络训练

文件keras为使用

```
```

### 使用已训练模型
