## Spark算子

### 从大方向来说，Spark大致可以分为以下两类：
- Transformation
  - 变换／转换算子；完成作业中间过程处理，不触发提交作业
  - 延迟计算：从一个RDD转换生成另一个RDD的转换生成另一个RDD的转换操作不是马上执行，需要等到有Action操作的时候才会真正运行
- Action
  - 行动算子；
  - 触发SparkContext提交Job，并将数据输出Spark系统；
### 操作数据类型分类
- Value数据类型的转换算子
- Key-Value数据类型的转换算子
- Action算子

### Value Transformation

#### 输入分区与输出分区一对一
- map算子
  - 原始RDD的每个元素通过map中的自定义函数映射转变为一个新的元素
- flatmap算子
  - 将原始RDD中的每个元素通过通过函数映射为新的元素，并将生成的RDD的每个集合中的元素合并为一个集合。
  - 比如，原始RDD中的元素是数组
#### 输入分区与输出分区多对一

#### 输入分区与输出分区多对多


distinct 去重
