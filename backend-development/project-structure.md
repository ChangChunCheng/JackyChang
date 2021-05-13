# Project Structure

現今大家所談論的Model View Controller, MVC架構是WebAPI最常見的開發方式。但是，本人在網路上爬文後發現自身對MVC的認識完全不是所認識的那樣，所以並不打算討論MVC，僅討論後端系統專案框架。這邊以Python FastAPI為例，運行環境使用Ubuntu 20.04、python virtualenv。

此框架可能不為最佳撰寫方式，事實上FastAPI文件中所使用的模組也並非以此方式建立。但說到RestfulAPI的框架，例如：NodeJS中的Express、Golang中的gin和Java中的Spring Boot等，會發現不管是任何語言的框架，其建立專案的模式大同小異，盡而使跨語言學習不需要額外花費太多的時間學習框架專案建立便能達到相同效果。

* project
  * .env： 環境設定檔，在運行過程中所需使用的環境變數，於Makefile中透過include .env使用
  * Makefile：利用make target及其能夠使用shell特性進行程式執行撰寫，不須重複敲打複雜的執行指令
  * bin：virtualenv建立的python相關執行檔
  * lib：virtualenv建立的套件路徑
  * include：virtualenv建立的環境相依工具
  * db：資料庫初始化、設定和儲存位置，可直接掛載storage或NAS
  * src：程式碼
    * main：程式進入點
    * config：後端系統運行設定
    * api：路由器與藍圖建立
    * loader：模組載入，資料庫連線、訊息處理器等皆在此載入
    * document：pydanticmodel，用於傳遞給client
    * service：系統服務、資料轉換、client與database間轉換程式，所有運算及商業邏輯皆在此
    * job：排程作業、事件處理
    * crud：資料庫CRUD\(create, read, update, delete\)操作
    * model：資料庫模型ORM定義



## Reference

* [MVC是一個巨大誤會](https://blog.turn.tw/?p=1539)
* [來談什麼是MVC](https://ithelp.ithome.com.tw/articles/10216225)
* [Clean Boilerplate of Go, Domain-Driven Design, Clean Architecture, Gin and GORM](https://dev.to/resotto/clean-boilerplate-of-go-domain-driven-design-clean-architecture-gin-and-gorm-2825)
* [詳解Nodejs Express.js專案架構](https://tw511.com/a/01/12394.html)

