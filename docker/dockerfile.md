# Dockerfile

Docker中，透過Dockerfile建立image並執行。可以透過分享Dockerfile，在不同機台上建立相同環境，只需要一行command即可完成。

* FROM：來源docker image，取用已建立的docker image再安裝其餘環境
* MAINTAINER：標籤docker image製作人
* COPY：複製本機檔案至docker image中
* ADD：與COPY相同，但來源可以是URL
* CMD：執行command
* ENV：環境變數設定
  * 若在同一ENV中設置多個環境路徑，後者不可使用前者環境變數
* ARG：暫存環境變數設定
  * 在image完成建立後，變數將不被保存
* VOLUME：將本機檔案或路徑掛載至image中
* EXPOSE：設定對外port
* WORKDIR：設定工作目錄
* USER：設定使用者

## Reference

* \*\*\*\*[**Docker -- 從入門到實踐：使用Dockerfile定制鏡像**](https://yeasy.gitbooks.io/docker_practice/image/build.html)\*\*\*\*
* Github：[ChangChunCheng/Docker-stack](https://github.com/ChangChunCheng/Docker-stack)

