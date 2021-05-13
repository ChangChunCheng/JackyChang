---
description: '本章節簡單說明Orient Relation Mapping, ORM/Orient Document Mapping, ODM應用。'
---

# ORM/ODM control

在後端系統開發時，若直接透過查詢條件撰寫SQL語法對資料庫進行查詢，其雖然能快速運行，但「安全」性問題隨之而來。在程式運行過程中，若遭惡意攻擊，將資料庫查詢語法植入程式時，會使得滲透者能夠隨意修改資料庫中的資料，導致資料錯誤或損毀。然而，使用ORM/ODM進行資料庫查詢時，其能有效阻擋滲透者利用資料庫語法直接利用伺服器進行植入\(因為根本無法執行\)。想當然而，使用ORM/ODM時因大量利用物件導向程式設計Object Orient Programming, OOP操作，導致其依賴程式語言本身特性與性能限制，變得效能較差。但是現今電腦運算速度每年成倍數成長的狀況下，搭配叢集資料庫\(cluster\)應用，例如：PostgreSQL/MariaDB on Hive、Casandra，使得此現象緩解不少，另現今的系統大多轉用ORM/ODM進行資料庫操作。

