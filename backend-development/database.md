---
description: 資料庫基礎操作
---

# Database

在資料日益增加的資訊時代，資料儲存與應用為一大問題。而「資料庫」就是因應各種資料儲存、查詢等各種應用需求而產生。日常處理資料大多使用Excel、Google Sheet等表單方式，甚至用csv, txt, tsv等文字結構。但此種資料儲存方式不僅造成占用容量大，也使得必須依靠完全人工管理，並難以根據需求去取得。此時，資料庫的存在就佔了極大優勢。

常見的資料庫有MS SQL、MySQL、Oracle Database等，完全開源方案也有像PostgreSQL、MariaDB等可以完全免費使用。上述所說屬於傳統的關聯式資料庫RDBMS \(Relational Data Base System\)，但近年來因應非特定結構與文章儲存而使用的NoSQL，例如MongoDB、Casandra等非關聯式資料庫。然而，每一種資料庫的設計與因應場景不同，並無法說用哪一個資料庫一定是最好。

#### 關聯式料庫 RDBMS

關聯式資料庫顧名思義，在其定義的資料中需建立資料表與資料表中的「關係」\(主鍵primary key、臨鍵foreign key\)，並且必須在表格建立時定義完成，且難以修改。所以在關聯式資料庫資料表建立前必須做非常多功課使得日後資料庫使用符合需求，例如：資料正規化。常見資料表設計方式是根據需求、專業領域知識\(同類型資料放一起\)、資料類型進行設計。另外，資料庫中表格建立時也必須定義其形態，\(data type/structure\)以便於資料儲存占用容量及搜尋時更方便。對資料庫表格設計有興趣者，強烈建議購買資料庫管理師執照的書來學習，並透過實際環境中所遇到的資料庫評估其設計及設計改善來學習。

關聯式資料庫查詢語法為SQL \(Structure Query Language\)，顧名思義為「結構式」查詢語法。透過SQL對資料庫進行查詢。SQL主要結構為select、from、where，並可搭配group by、order by、having等語法和sub-query方式進行複雜查詢或運算。學習SQL建議使用ANSI SQL，此為SQL設計的標準，表示ANSI SQL在每一種資料庫中皆可以使用\(每一個資料庫都有自行定義的特殊語法\)。

#### 非關聯式資料庫NoSQL

近年因為log資料在AI界被廣泛應用，並且搜尋需求的擴增，使得市面上有越來越多NoSQL出現。但本人並沒有NoSQL應用經驗，在此僅能簡單述說。NoSQL在定義時，不需要定義其資料型態、關係，並且可以以「任意」格式儲存，使得資料儲存變得更容易使用，其利用json格式進行資料倉儲。但也因為其並無太大限制，導致後續逕行資料處理問題變得困難。然而，在「文章搜尋」應用因非固定資料結構而使得其能發揮所長，例如：Elasticsearch、Solr等，在log處理與文章儲存被廣泛使用，其自帶搜尋引擎也被廣泛應用，減少許多開發成本。

#### RDBMS v.s. NoSQL

不論是關聯式資料庫或非關聯式資料庫，其應用場景不同，也並非一定要使用哪一套。建議進行系統規劃時，需多了解兩套系統的特性，例如：錯誤處理，方能更好的使用。



## Reference

* [SQL語法教學](https://www.1keydata.com/tw/sql/sql.html)
* GitHub: [TritonHo/slides](https://github.com/TritonHo/slides/tree/master/Taipei%202019-04%20course?fbclid=IwAR1BTZQBLY16bHtCvmpfak5yylb-vXEYMVUngS65Xfjz4rY9J4y0_fCoiBg)

