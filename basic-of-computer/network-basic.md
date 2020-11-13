---
description: 本章將以家用網路來介紹常用網路概念，若需要學習網路基礎概論如何架構，請參考鳥哥的 Linux 私房菜 - 基礎網路概念。
---

# Network Basic

網路是一種用於連接電腦間的通訊方式，其透過硬體位址 \(mac address\) 和 IP \(目前常用：IPv4，但正轉換為IPv6中\) 辨識與過濾其資料傳輸。\(詳見[鳥哥的 Linux 私房菜 - 基礎網路概念](http://linux.vbird.org/linux_server/0110network_basic.php)\)。本章中僅介紹基礎網路IP位址範圍 \(又稱網域\) 用途與常見家用網路架構。

* IPv4：IP為協議名稱，v4為第四代，稱第四代網路通訊協議。用於設備透過網路傳輸資料時辨識目的設備位置使用。IP位址由DHCP server \(於下方解釋\) 提供，並統一控管。 IPv4由4組0-255的數字組成，例如：1.1.1.1、1.0.0.1，由上述可知IPv4最多可以定位256x256x256x256台網路設備。然而，近十年來網路設備量大幅上升，IPv4顯然不足以使用。另一方面，並非所有網路設備皆「必須」在「任何地方」都可以「直接」連線使用，因此IP協議中還將特定IP範圍切割為區域網路IP或保留來辨識特定通訊條件 \(例如：0.0.0.0、127.0.0.1\)。 在此我們需要注意的是1. 哪幾個IP是常用於辨識特殊意義、2. 哪些IP範圍是用於組織內區域網路、3. 哪些IP範圍用於公用網路。

1. 常用特殊IP
   1. 127.0.0.1：表示設備自身，在任何網路設備上使用此IP，必會連線到設備本身。\(localhost也是常見用於測試時透過網路連線到自身的網域名，但與此IP有些許不同\)
   2. 0.0.0.0：表示任意設備。在使用網路的伺服器中，常需設定連線限制，若用此IP表示不限制任何連線IP，即任何設備皆可以使用。
2. 區域網路IP範圍：表示僅限於區域網路內使用。
   1. 10.0.0.0 - 10.255.255.255
   2. 172.16.0.0 - 172.31.255.255
   3. 192.168.0.0 - 192.168.255.255
3. 公用網路IP範圍：只要非前述所說的特殊用途IP外，其餘皆為公用網路IP位址。詳見[IP位址的組](http://kevin.hwai.edu.tw/~kevin/material/EAssistant/IP_Class.htm)。

* Mac address：所有電子設備在出廠前都會有mac address \(硬體位址\)，此位址是由組織協議發放，全世界所有設備要生產時皆必須申請硬體位址。

{% hint style="info" %}
實際上，區域網路管理設備是透過mac address和IP對照表確認網路傳輸對象，並非僅透過IP進行連線。
{% endhint %}

![](../.gitbook/assets/network-system-diagram.png)

以台灣來說，上圖中的Internet \(雲\) 可視為中華電信或其他網路業 \(統稱ISP\) 者提供的網路連線。其餘皆為家中的Wifi分享器 \(以下稱為路由器，Router\) 所管理的家中的設備。一般家用路由器中有Firewall \(防火牆\)、Gateway \(網路閘道器\)、DHCP server和Switch \(網路交換器\)功能。每個服務的功能如下：

1. Firewall 防火牆：用於防禦網路攻擊。
2. Gateway 網路閘道器：用於轉換不同網域間的通訊。
3. DHCP server：用於管理區域網路內設備IP。
4. Switch 網路交換器：用於網路中設備資料傳遞，可不透過DHCP server，直接利用mac address和IP對應表進行資料交換。

## Reference

* [鳥哥的私房菜](http://linux.vbird.org/linux_server/0110network_basic.php)
* [IP位址的組成](http://kevin.hwai.edu.tw/~kevin/material/EAssistant/IP_Class.htm)

