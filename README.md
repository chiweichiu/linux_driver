# linux_driver
<font color=#008000>艾蒂嵌入式學院的linux課程筆記。</font><br>
Raspberrt pi 3b 與其自制IO擴充板
![alt raspi3b](https://github.com/chiweichiu/linux_driver/blob/main/utils/raspi3b.JPG)
[stable/linux-4.14.y](https://github.com/raspberrypi/linux/releases/tag/raspberrypi-kernel_1.20190401-1)
<br>
<br>
## **Linux I2C Framework**<br>
透過linux i2c子系統，了解platform bus模型(linux device model)，<br>
其platform driver/platoform device架構(device tree)與client端driver，<br>
完整了解linux驅動程式框架。<br>
實例為i2c eerpom driver經過i2c framework，再透過i2c host controller發動command驅動。<br>
[Linux I2C Framework and eeprom driver](https://github.com/chiweichiu/linux_driver/blob/main/linux_i2c_framework/README.md)
- i2c framework / client driver / controller driver。
- i2c protocal overview。
- i2c eeprom 24c02c操作。
> Platform bus model(platform device/platform driver)
- TBD
## **Device tree**<br>
跟platform device架構很類似的新架構，都是針對作業系統有的硬體資源做描述，相比於platform device的優勢在於使用device tree可以動態<br>
對硬體資源做載入的動作，不需要重新編譯kernel image(在同一個編譯版本的kernel下)。能達成這種效果的理由是device tree是單獨的dts檔案<br>
，bootloader在開機時會把這個資訊傳遞給kernel，當作kernel開機參數之一。 
- DTS cource<br>
![alt bcm2710-rpi-3-b](https://github.com/chiweichiu/linux_driver/blob/main/utils/bcm2710-rpi-3-b.JPG)<br>
![alt vi-bcm2710-rpi-3-b](https://github.com/chiweichiu/linux_driver/blob/main/utils/vi-bcm2710-rpi-3-b.JPG)<br> 
[Linux Device Tree](https://github.com/chiweichiu/linux_driver/blob/main/linux_device_tree/README.md)  
## Linux SPI Framework
- TBD
## Linux UART Framework
- TBD
## Char device driver
- TBD
## GPIO Driver Framewrok
- TBD
## 中斷
- TBD
## 核心機制
- TBD

## Reference
- https://en.wikipedia.org/wiki/VideoCore#Table_of_SoCs_adopting_VideoCore_SIP_blocks
- https://github.com/raspberrypi/linux/tree/rpi-4.14.y
- https://www.raspberrypi.com/documentation/computers/linux_kernel.html#cross-compiling-the-kernel
