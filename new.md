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
│   └── corpus
│   │   │   source.txt
│   │   │   <corpus>
│   │   
│   └───models
│       │   output_graph.pbmm
│       │   alphabet.txt
│       │   ...
│   
└───glove
    │   glove.6B.100d.txt
```

根目录下为主要的训练及预测代码，其中`emotic_keras_training.py`、`emotic_keras_glove.py`为模型训练代码，`emotic_keras_test.py`为使用已训练模型的代码，`tools.py`包含一些工具函数。

在`data/`文件夹中放置原始数据集及数据集预处理代码。数据集通过`speech_to_text.py`进行语音转文字，通过`generate_corpus.py`进行数据集的预处理。`models/`文件夹中为一些DeepSpeech工具的模型。`corpus`文件夹中放置原始数据集，`source.txt`记录不同数据集的来源。

`glove/`文件夹中的为预训练的GloVe模型。

---

### 环境及工具

* Windows >= 7
* Python > 3.4
* pip >= 19.0
* tensorflow 2.x
* keras 2.x

---

### 数据集预处理

#### 语音转文字工具DeepSpeech

由于没有找到非常合适的语音数据集，因此这一步不是必须的。

安装DeepSpeech库

```
pip3 install deepspeech
```

语音转文字

```
python3 speech_to_text.py --model ./models/output_graph.pbmm --alphabet ./models/alphabet.txt --audio path/of/audio
```

#### 生成训练集和测试集 (generate_corpus.py)

文件中`path_corpus_original`为原始数据集的路径，`path_train_corpus`和`path_test_corpus`分别为基于原始数据集进行处理后生成的训练数据集和测试数据集的路径及名称。

如，将`data/corpus/tlkh.txt`放到`data/`下，并重命名为`text_emotion_original.txt`，直接运行文件：

```
python3 generate_corpus.py
```

生成两个文件`train.txt`和`test.txt`，分别为训练集和测试集。

---

### 神经网络训练

文件`emotic_keras_training.py`为使用one-hot和Skip-gram方法进行词嵌入实验的代码，而文件`emotic_keras_glove.py`为使用GloVe进行词嵌入的实验代码。

在`emotic_keras_training.py`中，通过修改`input_struct`选择不同的词嵌入方法，`'bag_of_words'`为one-hot方法，`'sequence_of_words'`为Skip-gram方法。通过修改`model_type`对神经网络的结构进行修改，或通过直接修改`# definition of the model`模块使用预设神经层进行网络构造。（也可以自定义层的结构，参考[编写你自己的Keras层](https://keras.io/zh/layers/writing-your-own-keras-layers/)。修改变量`path_train_txt`和`path_test_txt`从而指向训练集及测试集。

运行`emotic_keras_training.py`：

```
python3 emotic_keras_training.py
```

同理，在`emotic_keras_glove.py`中，通过修改`# definition of the model`对神经网络的结构进行修改，修改变量`path_train_txt`和`path_test_txt`从而指向训练集及测试集。

运行`emotic_keras_glove.py`：

```
python3 emotic_keras_glove.py
```

---

### 使用已训练模型进行单句情感预测

使用`emotic_keras_test.py`使用已训练模型进行预测，修改`phrase`变量改变需要预测的句子

运行`emotic_keras_test.py`：

```
python3 emotic_keras_test.py
```
