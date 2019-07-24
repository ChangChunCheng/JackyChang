# DataFrame Manipulation

Dataframe \(資料表\) ，在database中稱為table，若只取得其中的值而不取其欄位名稱、索引，也可以視為「2-dimension」matrix。Dataframe的設計，來源於統計學家對於資料的觀察方式。過去統計學家透過建立table來探索資料，但是一但他們要利用電腦取代手動運算時，往往因為專業知識不足，而無法利用像C語言中的array \(陣列\) 取代運算工作。\(至今，雖然大多的運算都由電腦取代，但仍然有不少統計學家不會撰寫程式\)

## DataFrame Manipulation

* apply：對每一筆資料進行指定運算。指定函數，將每一個raw data作為函數的輸入值。
* transpose：轉置。在matrix中，轉置即「行列互換」。但是在DataFrame中，又分為以下兩種：
  * unstack：將一個欄位分割成多個欄位。
  * stack：將多個欄位合併成一個欄位。
* group：以特定欄位中的值做分群，將每一個相同值的資料放在一起計算。
* agg/aggregation：對dataframe中指定欄位進行運算。通常搭配group使用，進行分組/分類運算。
* concat：合併，又分為以下兩種：
  * merge：左右合併，用於將多個表格中不同定義的資料透過key進行整合。
  * union：上下合併，用於多個表格有相同定義資料進行整合。
* 
