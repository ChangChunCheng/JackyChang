# Hardware

#### **本章會簡單討論電腦的執行流程與造成電腦執行速度的原因。** The pipeline of computer executing and the cause of the computer is slow.

電腦在執行任何一個工作時，必須將資料從硬碟 \(Hard Drive\) 讀取至記憶體 \(Random Access Memory, RAM\) 後，才可以被中央處理器 \(Center Process Unit, CPU\) 讀取並執行。其中，資料進入 \(Input\) 與輸出 \(Output\) 硬體動作簡稱為 IO \(Input/Output\)；資料寫入稱為 write，讀取稱為 read。

電腦執行程式的過程，從硬碟「讀取」程式與資料、「輸出」至RAM、「寫入」RAM再從記憶體「讀取」、「輸出」至 CPU ，再 CPU 中不斷地被「讀取」、「寫入」、「進入」與「輸出」，最後再以相同流程放回硬碟中。  
從上述的過程中可以看到，一個程式執行，有非常多的「讀取」、「寫入」、「進入」與「輸出」的動作，這些動作的速度決定的電腦的執行速度。

備註：  
本文不會講解各個硬體的功能與細部執行流程。

然而，現在的CPU與RAM的速度都已達到GB/s的程度，但是硬碟的讀寫速率大多在 100 MB/s 左右，即便是目前市面最快的 SSD \(Solid-State Disk\) 最快頂多1 GB/s ，遠不及 CPU 和 RAM 的讀寫速率。

為了解決上述的問題，往往會在伺服器配置與演算法設計上著手，例如：一台伺服器有多顆硬碟，利用磁碟陣列 \(Redundant Array of Independent Disks, RAID\) 做資料存取與資料備份，或是在程式設計時將程式、資料放在多顆不同硬碟，並利用設計好的流程對多硬碟同步存取，減少 IO 時間造成程式無法順利執行。

## Reference

* [鳥哥的Linux私房菜](http://linux.vbird.org/)
