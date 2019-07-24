# Batch Process

Batch process \(批次處理\) ，一次處理一批資料，這組資料可能是一次性取得，也可能是每過一段時間取得一次。

Github上，在andkret/Cookbook中對batch process有以下描述：

{% hint style="info" %}
Batch processing is something you do either without a schedule or on a schedule \(tax statement\). It is used to ask the big questions and gain the insights by looking at the big picture.
{% endhint %}

在公司內部，一個部門要分析特定資料，往往會向資訊部門索取資料，而資訊部門提供資料的方式除非特定需求或是特定資料庫，否則都是透過資訊部門取得資料後再交由提出需求的部門使用。而這樣的動作往往是因為非常態事件發生或是進行新企劃探索 \(without a schedule\) 或是每一個月、每一季或是年度報表 \(on a schedule\) 的需求而索取的。

在技術層面，過去的CPU執行速度緩慢，無法達到需求，而有了parallel process的概念產生，只要運算邏輯上不相互影響，就可以使多個工作同時執行，造就了多核心的CPU出現。而在batch process中，為了使處理資料時間縮短，而且盡可能使用CPU完整效能，在batch process相關的演算法與工具上，都使用了parallel process方式，達到了高效率的執行，例：SQL \(structure query language\)、matrix calculation、dataframe manipulation等。

{% hint style="info" %}
為了使硬體可以更有效率進行運散，大部分的運算工作，都依靠著工作流程設計、演算法設計做成batch process模式。
{% endhint %}

## Reference

* Github：[andkret/Bookbook](https://github.com/andkret/Cookbook)

