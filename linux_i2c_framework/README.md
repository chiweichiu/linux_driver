# linux i2c framework
> Software stack<br>

![alt Software stack](https://github.com/chiweichiu/linux_driver/blob/main/utils/i2c_sofeware_stack.JPG)
- 右半i2c host controller或者稱i2c adapter(即platform_device(resource)) 對應一個 adapter dirver(platform_driver)
- 左半i2c driver實際上是夠拓i2c core->i2c adapter->i2c controller對bus送訊號去跟client device通訊

> Reference<br>
- https://www.slideshare.net/itembedded/raspberry-pi-linux-i2c-driver#13
