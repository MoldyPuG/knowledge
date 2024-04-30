Data Engineerに必要なApache Sparkの知識を問う面接の例題 <br>
Ref: [Most Commonly Asked Apache Spark-Based Conceptual Questions in Data Engineer Interviews](https://blog.stackademic.com/most-commonly-asked-big-data-apache-spark-concepts-in-data-engineer-interviews-856af11f397c)

## Why Apache Spark is an efficient data processing framework as compared to Hadoop. Why?
There is a difference at a Processing Model.

**Processing Model:**
> - **Hadoop**: Hadoop primarily relies on a batch processing model, where data is stored in the Hadoop Distributed File System (HDFS), and batch jobs (MapReduce) are executed on this data. It’s suitable for batch-oriented processing.
>
> - **Spark**: Spark supports both batch processing and real-time data processing. It introduces the concept of Resilient Distributed Datasets (RDDs), which allows for in-memory data processing and iterative processing, making it more versatile for various use cases.

As a result from the difference of the Processing Model, Spark is up to 100 times faster for certain workloads.

![Spark processing model](<../img/spark_processing_model.png>)

Ref: [Major Difference Between Spark and Hadoop](https://medium.com/@arpitpadwekar/major-difference-between-spark-and-hadoop-dfe75f664b70)

### Answer
Q. Why Apache Spark is an efficient data processing framework as compared to Hadoop. Why?

Sparkはreal-time data processingを提供しており、Hadoopのように中間処理を一回一回ストレージに書き出す必要はなく、インメモリで処理できることで最大100倍近くHadoopより早くなり得る。
