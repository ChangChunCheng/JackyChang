# Linux Command

想要學習如何在 Linux 中建立環境，必須學會一些基礎指令 \(command\)。實際建立伺服器時，常因為效能考量而不會使用有 GUI \(Graphic User Interface\) 的機器，而是僅能利用 command 進行佈署 \(deploy\) 與管理工作。

常見指令如下：

* sudo : superuser do, 使用超級使用者 \(root\) 執行指令
* apt-get install : 查詢軟體並安裝
* echo : 顯示內容
* touch : 建立文件
* mkdir : 建立目錄
  * -p : 可建立槽狀目錄
* mv : 移動資料
* cp : 複製文件
  * -r : 複製目錄下所有文件
* ls : 顯示目錄下所有文件
  * -a : 顯示文件訊息
* cd : 移動所在路徑
* chmod : 設定檔案權限
* chown : 設定檔案擁有者與擁有群組
* grep : 搜尋檔案中文字
* awk : 文字處理
  * 利用標準輸入輸出 \(standard in / standard out, stdin/stdout\) 進行逐行處理
* ssh : 遠端連線、資料傳輸
  * 利用 TCP/IP 進行網路連線與資料傳輸

Ubuntu 中，預設 ll = ls -a 為顯示目錄下文件訊息，範例如下：

```text
-rwxr-xr-x 2 root root 48 2013-11-27 16:34 test
```

上列範例說明：

1. 開頭的 -，表示此檔案為文件。常見有 "-", "d", "l"，分別為文件、目錄與連結。
2. 上述 rwxr-xr-x 可分割為三組rwx，可看為\(rwx\)\(r-x\)\(r-x\)。其中 r 是read、w 是 write、x 是 execute。第一組為  Owner 使用權限、第二組為 Group 使用權限、第三組為 Other \(即非擁有者也非該群組成員\) 使用權限。 此範例中，擁有者可 讀、寫、執行此文件，其他人僅可讀取與執行此文件。

除了上述的常用指令外，每個指令皆有細部選項 \(argument, arg\) 與使用技巧，另外需認識 group, owner \(參考鳥哥的私房菜\)。



## Reference

* [鳥哥的私房菜](http://linux.vbird.org/linux_basic/0210filepermission.php)

