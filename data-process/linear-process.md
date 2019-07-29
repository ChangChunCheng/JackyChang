# Linear Process

Linear process \(線性處理\) ，讓資料像在流水線上，一次只處理一筆。通常用於即時性 \(real time\) 資料蒐集，例：logs。其中，像pipeline、streaming也都屬於類似linear process的概念。

Linear process在規劃處理方法及撰寫程式上通常不會遇到太困難的問題。在linux command中，也有一些command的概念也是利用linear process來實作，例：awk、sed、grep等。

Linear process雖然概念簡單，但是當談論到資料與資料間的關係，例：成長率、事件發展順序，就容易產生出許多難以發現的邏輯問題，其中最重要的問題是資料「排序」。

## Reference

* Github：[andkret/Bookbook](https://github.com/andkret/Cookbook)

