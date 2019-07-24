# Cluster Management

除了建立機台，機台也可能因為操作不當、bug等原因造成crash的問題。然而，在現今每一套系統都獨立的情況下，要維運人員對在短時間內修復機台並不是件容易的事。為了維護更方便，而有了叢及管理系統 \(cluster management\)。

## Docker swarm

Docker swarm是docker官方開源的container管理系統，讓使用者在無需學習太多新技術的情況下可以透過系統自動化管理各個機台，並取得機台即時狀況。

Docker swarm可接受docker command，甚至是直接支援docker-compose的使用 \(有部分功能差異\)，讓使用者從單機測試至多幾佈署時，可以不需要大動作更改程式。

Docker swarm中相較其他叢集管理系統的優勢在於，節點的新增與淘汰，僅需要一行command就可以完成。

{% hint style="info" %}
Docker swarm在安裝docker時會自動安裝。

Docker swarm使用時，需注意每個節點上是否有相同的image和可連線到指定registry。
{% endhint %}

## Kubernetes

由Google開源的kubernetes \(k8s\)，在過去僅用於Google Cloud Platform中，然而其強大的佈署、容錯能力，使得大家對其的關注度極高。在2019年，Microsoft也將k8s導入其自家雲端系統Azure上。

Kubernetes強大於microsoft service佈屬和容錯能力，能在極短的時間內建立完成。而k8s底層機台也是由docker實現，並且支援docker swarm使用。簡單來說，使用kubernetes可以使會使用docker swarm的管理人員更容易學習k8s，進入大量microsoft service管理。

然而，kubernetes學習成本高、學習時間長，若對於系統理解程度不夠，很容易因此而畏懼系統，不建議對系統認知不足的人投入。

{% hint style="info" %}
Kubernetes是針對大量機台管理及服務而設計建立出，本身不支援單機運作。可以透過官方提供惡minikube、kind \(k8s in docker\)、dind \(docker in docker\) 工具學習。
{% endhint %}

現今的叢集管理系統不僅僅是維護節點正常運行，也透過備份、同步模式實現難以損毀的工作環境，而在之中也從系統層面加入了工作負載平衡的功能，使得後續提及的任務調度系統減少crash的機率。

## Reference

* \*\*\*\*[**Docker —— 从入门到实践：**Docker 三剑客之 Docker Swarm](https://yeasy.gitbooks.io/docker_practice/swarm/)
* \*\*\*\*[**Docker —— 从入门到实践：Kubernetes**](https://yeasy.gitbooks.io/docker_practice/kubernetes/)\*\*\*\*

