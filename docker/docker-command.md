# Docker Basic

* image : 環境映像檔，類似於作業系統的ISO檔。
* container : 容器 \(貨櫃\)，執行環境的單位。
* registry : 倉庫，用於存取docker image的地方。
  * 本機docker有放置docker image的位置，也可以透過pull、push指令與公有/私人 \(public/private\) docker registry存取docker image。
  * public docker registry : https://hub.docker.com
  * private docker registry : 可透過官方提供的private registry建立私人docker registry伺服器。

{% hint style="info" %}
Docker中，image為靜止的環境，container為執行中的環境。執行工作前，必須將image啟動為container才可進行運算。
{% endhint %}

* * docker version : docker版本
* docker info :  docker版本訊息
* docker search : 搜尋images。未設定registry IP時，預設搜尋public docker registry
* docker pull : 從registry抓取image
* docker push : 將image放置registry
* docker images : 機台中的image
* docker ps : 機台的container
* docker run : 透過image產生container
* docker exec : 指定image執行command
* docker attach : 進入container
* docker logs : 索取container logs
* docke rm : 移除container
* docker rmi : 移除image
* docker imspect : 查看container詳細訊息
* docker rename : 對container重新命名
* docker cp : 從container複製檔案到機台
* docker save : 將image存為.tar
* docker load : 將.tar轉為image
* docker export : 將container存為.tar
* docker import : 將.tar轉為container
* docker kill : 刪除container



## Reference

* \*\*\*\*[**Docker 初學筆記 - 基本指令操作教學**](https://blog.longwin.com.tw/2017/01/docker-learn-initial-command-cheat-sheet-2017/)\*\*\*\*

