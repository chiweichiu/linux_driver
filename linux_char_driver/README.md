# linux device tree
> linux driver overview<br>
---
![alt linux_driver_overview](https://github.com/chiweichiu/linux_driver/blob/main/utils/linuxdriveroverview.jpg)<br> 
- 上層是透過open(system call)/dev/xxx檔案(檔案系統)的概念，去呼叫driver的function控制對應的硬體動作。<br>
- 以byte為單位傳輸，大部分周邊元件或感測器都屬此類。<br>
- major number代表某一支driver，minor number代表同一支driver對應不同的device。<br>
- struct file_operations : 所有device的操作，都是實作這個裝置。<br>
- struct file : file_operations的參數，當使用者open這個device時，Kernel會自動配置file這個結構，來代表一個檔案，<br>
                會記錄open時的權限，紀錄讀寫位置(f_pos)，open返回的fd，即是file結構的實體。<br>
- struct inode : Kernel內部用來表示file的一個結構，程式open一個inode會得到一個file實體，兩個程式同時open一個inode，<br>
                 會得到兩個file結構，major/minor number就藏在inode裡面。<br>

> Reference
- 
