
Data Engineerに必要なApache Sparkの知識を問う面接の例題 <br>
Ref: [Most Commonly Asked Apache Spark-Based Conceptual Questions in Data Engineer Interviews](https://blog.stackademic.com/most-commonly-asked-big-data-apache-spark-concepts-in-data-engineer-interviews-856af11f397c)


## Explain the main components of Apache Spark Architecture and how they interact with each other
### Components
SparkのComponentは以下のように構成される。<br>

![Spark Components](<./img/spark_component.png>)

SparkのMain Componentは何かと問われたら、その問いは主に以下に分類できる。
1. Driver Program <br>
  a. Spark Context
2. Cluster Manager
3. Worker Node <br>
  a. Executor

Ref: [Cluster Mode Overview](https://spark.apache.org/docs/3.5.1/cluster-overview.html#components)

**Driver program**
> The process running the main() function of the application and creating the SparkContext

どのようにしてSpark Driverは機能するか？
1. ユーザープログラムから演算やデータの要求を受け取る
2. taskをステージに分割し、DAG Schedulerに送信する
3. DAG SchedulerはtaskをステージにまとめDAGを構築する
4. RDDはステージ間のデータフローを管理する
5. タスクはTask SchedulerによってSpark executors上でスケジュールされる

ちなみに、Spark Contextとは
> SparkContext represents the connection to a Spark cluster, and can be used to create RDDs, accumulators and broadcast variables on that cluste

Ref:[ What is Apache Spark Driver](https://medium.com/@ashwin_reddy_/what-is-apache-spark-driver-509653ab750a)

**Cluster Manger**
> An external service for acquiring resources on the cluster (e.g. standalone manager, Mesos, YARN, Kubernetes)

Cluster上で実行するために、SparkContextはアプリケーション全体にリソースを割り当てるCluster Mangerに接続される。<br>

Ref: [Apache Spark Cluster Managers](https://medium.com/@malli3131/apache-spark-cluster-managers-67d190075048)

**Worker Node**
> Any node that can run application code in the cluster

**Executer** : 
Sparkジョブの個々のタスクの実行を受け持つワーカープロセス。ExecutorはSparkアプリケーションの起動時に1度起動されて、通常はそのアプリケーションが動作している間、動作し続ける。アプリケーションを構成するタスク群を実行し、結果をドライバに返す。
ユーザプログラムによってキャッシュされるRDDをのためのインメモリストレージを各Executor内で動作するブロックマネージャーと呼ばれるサービスを通じて提供する。<br>

Ref: [Apache Sparkのコンポーネントを整理する](https://qiita.com/zumax/items/8accafee546d244fd93e)

### Answer
Q. Explain the main components of Apache Spark Architecture and how they interact with each other?

Sparkのmain componentsとしては主に、Driver、Cluster Manager、Worker Nodeが挙げられる。
Driverはユーザーからのリクエストを受け取り、SparkContextを通じて、Spark Clusterを動かしていく。その中で、Cluster MangerがResourceの取得、管理を行う。振り分けられたResourceに応じて、Worker Node内で、実際の演算等を行うExecuterが起動され、データ処理を行う。最終的にDriverに結果が返され、ユーザーへも結果が返される。
みたいなイメージ。
