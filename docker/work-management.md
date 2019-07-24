# Work Management

在今日，已經有許多運算工作是單一台電腦無法負荷的，而有了許多運算調度的系統出現，例：Hadoop、Spark、Mesos等。

## Hadoop

Hadoop的用途在於一個龐大的運算任務，無法僅透過一台電腦完成，而將工作拆分至不同節點上進行運算，進而完成龐大的運算任務。

* HDFS：Hadoop的檔案系統，負責管理檔案。在Hadoop中，任何想索取檔案的工作，皆必須經由HDFS提供。
* YARN：Hadoop的運算系統，負責進行運算任務調度。當使用者丟一個程式給Hadoop進行運算時，必須經由YARN執行。
* Resource Manager：負責監控、管理節點資源，提供YARN、HDFS能使用的資源訊息。

## Mesos

Mesos是一個任務調度器。使用者在Mesos上建立節點，並告知該節點負責的工作項目時，由Mesos決定新進任務要指定給哪一個機台運算。

然而，Mesos原先目的在於提供多台機器執行大量相同工作，而且這些工作的運算量都不大。近幾年，由於Docker swarm、Kubernetes等叢集管理系統都有了自動平衡負載的功能，Mesos成了一個過渡產品。

## Spark

