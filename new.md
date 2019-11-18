## ？

### 项目结构

```
project
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

### 数据集预处理

#### 语音转文字工具DeepSpeech

