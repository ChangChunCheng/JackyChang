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

Spark是一個工作管理系統，其目的只用於資料運算處理。Spark的「in memory」的特性使得使用者的機台必須擁有大量的記憶體以滿足運算需求。然而，Spark本身有自帶的節點管理器，用於在不同機台之間進行相同運算，以達到高度平行化。但是其本身的節點管理器並無法有效支援不同的工作類型，使得大家習慣搭配其他系統一同使用。

過去，Spark針對Mesos建立起任務調度器，但是近年來因Hadoop崛起，Spark本身也開始支援Spark on YARN運算模式。

## Reference

* \*\*\*\*[**Day 2 - Hadoop Ecosystem 之 Hadoop 介紹**](https://ithelp.ithome.com.tw/articles/10190756)\*\*\*\*
* \*\*\*\*[**Docker —— 从入门到实践：**Mesos - 优秀的集群资源调度平台](https://yeasy.gitbooks.io/docker_practice/mesos/)\*\*\*\*
* \*\*\*\*[**Apache Spark 簡介**](https://ithelp.ithome.com.tw/articles/10194895)
* \*\*\*\*

