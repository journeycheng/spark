# spark

### spark和hadoop的对比
- 原生语言：hadoop－java，spark－scala
- 计算模型：hadoop-mapreduce, spark-DAG。经常有人说spark是内存版的MapReduce，实际上不是的。spark使用的是DAG计算模型可以有效地较少Map和Reduce任务之间传递的数据。
- 存储：hadoop-HDFS, spark-RDD,HDFS。
- 对于数据的操作种类更多。两个集合的交并补等，spark都有函数直接计算，而hadoop实现这样的计算无比繁琐，所有的事情必须要转化为两个操作Map／Reduce。
- 应用场景：Hadoop更适合做批处理，Spark更适合做需要反复迭代的机器学习
- spark继承了MapReduce的线性扩展性和容错性
- spark扩展了内存计算能力，RDD抽象使开发人员将流水处理线上的任何点物化在跨越集群节点的内存中，后续步骤如果需要相同数据集时就不必重新计算或从磁盘加载
- **构建数据应用的最大瓶颈不是CPU、磁盘或者网络，而是分析人员的生产率。**通过将预处理到模型评价的整个流水线整合在一个编程环境中，Spark大大加速了开发过程。
- Spark从根本上是为性能和可靠性而生的。由于构建于JVM之上，它可以利用许多Java技术栈里的操作和调试工具
- 流式处理组件Spark Streaming能连续从Flume和Kafka之类的系统读取数据
  
  
  
  
  
### wordcount
- python版本
```python
from pyspark import SparkContext, SparkConf
appName = 'WordCount'
conf = SparkCong().setAppName(appName).setMaster('local')
sc = SparkContext(conf)

inputFiles = 'input/*'
outputFile = 'output/result'

inputRdd = sc.textFile(inputFiles)
wordcounts = inputRdd.flatMap(lambda line: line.split(' ')).map(lambda word: (word, 1)).reduceByKey(lambda x,y: x+y)
wordcounts.saveAsTextFile(outputFile)
```

- scala版本
```scala
import java.io.File
import scala.io.Source

object WordCount{
    def main(args: Array[String]){
        val dirfile = new File("wordcount")
        val files = dirfile.listFiles
        val listFiles = files.toList
        val wordsMap = scala.collection.mutable.Map[String, Int]()
        listFiles.foreach(file => Source.fromFile(file).getLines().foreach(
            line => line.split(" ").foreach(
                word => {
                    if (wordsMap.contains(word)){
                        wordsMap(word) += 1
                    }else{
                        wordsMap += (word -> 1)
                    }
                }
            )
        ))
        for ((key, value) <- wordsMap) println(key + ":" + value)
    }
}
```
