# What is docker ?

隨著硬體的發展，現今的電腦設備可以進行更高效的運算。然而，在這樣的背景下，大多數的app所需要的硬體運算需求並沒有如此大量的需求，而產生了「單機多工」的運作模式，加上app需要依賴作業系統環境而有了container的構想，並產出作業系統虛擬化的軟體，例如：Oracle VirtualBox、VMware的各種產品、Microsoft Hyper-V，和在Linux中被應用於伺服器的就是Linux Container \(Linux Container\)。

![&#x5716;&#x7247;&#x4F86;&#x6E90;&#xFF1A;Docker &#x2014;&#x2014; &#x5F9E;&#x5165;&#x9580;&#x5230;&#x5BE6;&#x8E10;](../.gitbook/assets/image.png)

上圖所示。不論是上述何種產品，皆是透過硬體層的虛擬化技術達到在一台電腦中建立多個作業系統工作環境，而達到多工的目的。在如此的情況下一台電腦必須負荷機台本身作業系統、執行虛擬化的軟體和在軟體中執行的作業系統。以在Windows下透過VMware安裝Ubuntu為例，電腦必須負荷2套完整作業系統的維運和軟體運作的運算，需要使用相當多的運算資源。

![&#x5716;&#x7247;&#x4F86;&#x6E90;&#xFF1A;Docker &#x2014;&#x2014; &#x5F9E;&#x5165;&#x9580;&#x5230;&#x5BE6;&#x8E10;](../.gitbook/assets/image%20%281%29.png)

為了達到減少硬體資源的浪費，在Docker環境中，透過Docker engine在本機作業系統上建立獨立的虛擬環境，以達到工作環境獨立的目的。其中，所有的工作環境的硬體操作都必須通過Docker engine向本機作業系統進行硬體操作。在Docker中，所有的虛擬環境都只保留了執行工作的必要核心，達到了減少硬體資源浪費的目的。

* image : 環境映像檔，類似於作業系統的ISO檔。
* container : 容器 \(貨櫃\)，執行環境的單位。
* registry : 倉庫，用於存取docker image的地方。
  * 本機docker有放置docker image的位置，也可以透過pull、push指令與公有/私人 \(public/private\) docker registry存取docker image。
  * public docker registry : https://hub.docker.com
  * private docker registry : 可透過官方提供的private registry建立私人docker registry伺服器。

{% hint style="info" %}
Docker中，image為靜止的環境，container為執行中的環境。執行工作前，必須將image啟動為container才可進行運算。
{% endhint %}

## Reference

* \*\*\*\*[**Docker —— 從入門到實：什麼是Docker**](https://philipzheng.gitbooks.io/docker_practice/content/introduction/what.html)\*\*\*\*



