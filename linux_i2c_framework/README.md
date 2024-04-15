# linux i2c framework
> **Software stack**<br>
---
![alt Software stack](https://github.com/chiweichiu/linux_driver/blob/main/utils/i2c_sofeware_stack.JPG)
- 右半i2c host controller(即在SOC裡面的IP元件)或者稱i2c adapter(即platform_device(resource)) ，對應一個 adapter dirver(platform_driver)。
- 左半i2c driver實際上是夠拓i2c core->i2c adapter->i2c cont**roller對bus送訊號去跟client device通訊。
- i2c-core是i2c管理層，整個子系統核心架構部分，負責解譯i2c msg，作為deivce driver與adapter溝通用。client driver與controller driver都需要跟i2c core註冊，
  一個晶片上是可以有兩個以上host controller，兩個以上controller的原因是i2c裝置有快慢之分，可以將不同i2c速度的裝置分開接到不同controller，
  這樣快速裝置就可以不用等慢速裝置。
- i2c-dev是kernel已經建立好的對上層的架構，當你export /dev/i2c-0(adapter-0) /dev/i2c-1(adapter-1)，可以用來寫user space driver，
  user space driver適用於用不了太多kernel結構或者像是讀溫度這種可以慢慢回給上層的應用，若是eeprom這種應用，就需要寫一個client driver。
  [linux i2c source](https://github.com/thenaran/linux-rpi/blob/master/drivers/i2c/)
- linux-rpi/drivers/i2c/busses/ - host controller driver。
- linux-rpi/drivers/i2c/algos - i2c msg包裝SDA SCL資訊轉換成實際protocal訊號。
- /sys - 透過sysfs bin_attribute結構時做一個bin file介面，把eeprom當作一個file去操作。

> **i2c client driver for eeprom**<br>
---
![alt Software stack](https://github.com/chiweichiu/linux_driver/blob/main/utils/i2c_client_driver.JPG)
- struct i2c_board_info裡，"at24"名稱可以隨便取，但slave address 0x50是唯一的，platform_data描述eeprom相關資訊，
  寫完後就透過i2c_register_board_info註冊到adapter裡面，其參數bus代表掛載在哪個i2c adapter裡。
- client device有個對應的driver透過struct i2c_driver去描述，裡面至少會實作probe/remove，還包含id_table，其概念
  是同一支driver支援不同的裝置。寫完透過i2c_add_driver註冊進子系統。
- probe呼計的時機點是client driver的name = board_info的name。probe時kernel帶兩個參數給driver，一個是i2c_board_info
  資訊，一個是kernel找到的這筆device id
> Reference<br>
- https://www.slideshare.net/itembedded/raspberry-pi-linux-i2c-driver#13
- https://www.kernel.org/doc/html/latest/i2c/writing-clients.html
- https://www.cnblogs.com/cslunatic/archive/2013/06/13/3134607.html
- https://hackmd.io/@RinHizakura/BJDTZnUsF
