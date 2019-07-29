# Pipeline

不論在 Linux 還是 Windows 作業系統中，在程式執行時皆有 "pipeline" ，而 pipeline 重點在於蒐集程式執行期間透過 stdout 輸出的內容，並傳遞給作業系統，再由作業系統整合給下一個程式。

pipeline 之所以重要，是因為其透過 stdin/stdout 與作業系統之間傳遞資料，而不是透過 input/output 對硬碟存讀資料，使得程式間的資料傳遞變得更有效率，而比較不被受限於儲存裝置的速度。

以 Linux command line 為例，

```text
$a.py | b.py
```

上列程式中， "a.py" 程式透過 sys.stdout 將資料傳遞給作業系統，並透過作業系統的 pipeline, "\|", 傳遞給 "b.py"，其中 "b.py" 也需透過sys.stdin來取得作業系統傳遞來的資料。

然而， pipeline 不只存在於程式與作業系統間，也常被用於資料流的設計中。例如：Python的Pandas套件中有pipeline方法，使得開發者可以使用它讓資料可以一次性完成所有運算工作，而不是逐步執行，減少Python解釋器所帶來的效能低弱的問題。

## Reference

* [鳥哥的私房菜](http://linux.vbird.org/linux_basic/0210filepermission.php)

