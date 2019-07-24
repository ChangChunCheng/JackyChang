# Addition

現實的系統中，不存在「單獨」使用一種方法實現的資料流處理，往往要多做搭配，將每個不同工作模式拆解開，用以設計最合適的方法。

以SAS為例，SAS的data step進行資料讀取時，第一步將一次讀取數筆 \(預設為5\) 資料，進行where篩選後，再逐筆傳至PDV中進行後續運算，並進行輸出。在整個過程中，第一步使用了batch process的方法，而後使用了linear process，實現最佳流程設計。

在reinforcement learning中，透過Q-table蒐集使用者回應資料，進行再訓練模型時，蒐集使用者log為linear process，但蒐集數千、甚至數萬筆資料後才進行再訓練，則是用batch process，以達到最佳流程設計。

近年來，有關big data的崛起，使得許多針對處理資料、執行大量運算的系統相擁而出，例：Hadoop、Spark、Apache Beam、Apache Kafka等。Hadoop透過高度平行化，在YARN上讀取HDFS中的資料進行同步運算；Spark RDD在nodes上進行同步運算使得batch proces方式將單台電腦記憶體容量限制拓展到多台電腦上，大幅度增加了運算量。由Google開源的Apache Beam和Apache Kafka則透過pipeline模式，直接監控並取得logs，是典型的linear process模式。

