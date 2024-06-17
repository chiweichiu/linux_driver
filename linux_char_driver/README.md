# linux device tree
> linux driver overview<br>
---
![alt linux_driver_overview](https://github.com/chiweichiu/linux_driver/blob/main/utils/linuxdriveroverview.jpg)<br> 
- 上層是透過open(system call)/dev/xxx檔案(檔案系統)的概念，去呼叫driver的function控制對應的硬體動作。<br>
- 以byte為單位傳輸，大部分周邊元件或感測器都屬此類。<br>

> Reference
- 
