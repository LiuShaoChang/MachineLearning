# 创建一个文本分类模型
> 训练一个机器学习模型去区分自然语言文本
## 概述
如图所示,text classifier就是一个被训练过的机器学习模型,用来识别自然语言的表达方式,如一个句子表达出来的情感.

<div align="center"><img src="./01.jpg" alt="图片01"></div>

你可以通过向模型提供大量的已经标记过的文本样例来训练它,例如,已经标记了积极的,消极的,中立的等标签的电影评论.
<div align="center"><img src="./02.jpg" alt="图片02"></div>

## 导入数据
首先,我们应该收集文本数据,并将它导入给一个`MLDataTable`实例.你可以创建一个JSON格式和CSV格式的数据表,或者,如果你的文本数据收集在文件中,你可以以文件夹的方式进行区分,用文件夹的名字作为标记,就像之前我们创建图片分类模型时用到的图片数据源一样.<br>
作为示例,我们可以创建一个JSON文件,其中包含我们已经根据情绪分好类的电影评论.每个条目都包含一对键,`text`和`label`.这些键的值就是用来训练模型的输入样本.如下所示:
```
[
    {
        "text": "The movie was fantastic!",
        "label": "positive"
    }, {
        "text": "Very boring. Fell asleep.",
        "label": "negative"
    }, {
        "text": "It was just OK.",
        "label": "neutral"
    } ...
]
```
在macOS playground中,用`MLDataTable`的`init(contentsOf:options:)`方法创建数据表
```
import CreateML

let data = try MLDataTable(contentsOf: URL(fileURLWithPath: "<#/path/to/read/data.json#>"))
```
