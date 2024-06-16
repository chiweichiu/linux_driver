# linux device tree
> device tree架構<br>
---
![alt dt](https://github.com/chiweichiu/linux_driver/blob/main/utils/dt.JPG)<br>
- 透過dtc編譯dts產生dtb(二進制檔案)。
- dtsi就是被dts include進來的檔案，dtsi描述某一顆晶片，同一顆晶片可以被用在不同的板子上，<br>
  只是周邊不同，那soc晶片描述就可以直接include進來，不需要重複寫。
- bcm2835/bcm2836/bcm2837(pi-3b)不同板子上周邊不同，但都用同一顆soc的描述。
- dts已經編譯成dtb燒錄進flash裡，若想開關某個硬體裝置，只需要用overlay.dts去覆蓋原本的內容即可。
- 有機制可以決定overlay.dts會不會生效
> 觀察系統的device tree<br>
---
- 使用dtc反向編譯<br>
![alt dts_cmd](https://github.com/chiweichiu/linux_driver/blob/main/utils/dts_cmd.JPG)<br>
![alt dts_cmd_2](https://github.com/chiweichiu/linux_driver/blob/main/utils/dts_cmd_2.JPG)<br>
- /arch/arm/boot/dts/bcm283x.dtsi<br>
![alt bcm283x](https://github.com/chiweichiu/linux_driver/blob/main/utils/bcm283x.JPG)<br>

> Reference
- https://www.slideshare.net/itembedded/linux-device-tree
