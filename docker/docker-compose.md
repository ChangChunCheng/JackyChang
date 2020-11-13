# Docker-compose

docker-compose是官方釋出的部署工具之一，可快速搭建container並有效控制container之間的關係。

docker-compose可以作為docker command的替代工具，將過去把system command自行撰寫成script的工作變成撰寫.yaml檔，以更明確、方便且簡單的方式建立環境。

## docker-compose.yaml

{% hint style="info" %}
docker-compose.yaml \(或.yml\) 可視為docker run指令變為腳本程式執行
{% endhint %}

* version：指定docker-compose版本
* service：啟用服務內容
* service\_name：此為jupyterserver，命名service在docker中名稱
* build：指定Dockerfile路徑
  * 此處可用image直接指定image名稱
* depens\_on：指定相依的service名稱，此service必須定義在相同docker-compose下
  * 定義service相依性，使用者無法在未關閉當前container下關閉相依container
* volumes：掛載本機路徑至conatiner中路徑
* command：container執行後執行的指令
* networks：給定docker DNS中網路名稱
* ports：將container port掛載至本機port
* tty：持續在背景執行，若container發生錯誤，將自動重啟

{% code title="example.yaml" %}
```text
version: "3"
services:

  jupyterserver:
    build: ./
    container_name: jupyter-server
    volumes:
      - ./jupyter/jupyter_notebook_config.py:/root/.jupyter/jupyter_notebook_config.py
      - ./app:/app
    command: bash -c "/opt/Anaconda3/bin/jupyter notebook /app"
    networks:
      - jupyter
    ports:
      - "8888:8888"
    tty: true

networks:
  jupyter:
    driver: bridge
```
{% endcode %}

透過docker-compose建立docker container時，docker-compose會重新定義container名稱，以免與其他執行中的container產生衝突，也會將docker-compose.yaml中定義的container同步管理。若要重啟服務，僅需要回到目錄下透握docker-compose重新建立或啟用即可。

* docker-compose build：建立當前目錄下docker-compose.yaml中給定的image
* docker-compose up：啟動當前目錄下docker-compose中給定的container
  * -d：在背景執行
* docker-compose down：關閉當前目錄下docker-compose中給定的container

## Reference

* \*\*\*\*[**Docker —— 从入门到实践：**Docker Compose 项目](https://yeasy.gitbooks.io/docker_practice/compose/)
* Github：[ChangChunCheng/Docker-stack](https://github.com/ChangChunCheng/Docker-stack)

