# 逐飞派引脚功能复用表

鬼知道逐飞何时发个官方的复用表，真是要硬件老命

注：本项目基于[龙芯2k0300数据手册](https://www.loongson.cn/uploads/images/2025060909245168407.%E9%BE%99%E8%8A%AF2K0300%E5%A4%84%E7%90%86%E5%99%A8%E6%95%B0%E6%8D%AE%E6%89%8B%E5%86%8C_V1.01.pdf)与[逐飞核心板原理图](https://gitee.com/seekfree/LS2K0300_Library/raw/master/%E3%80%90%E5%8E%9F%E7%90%86%E5%9B%BE%E3%80%91%E5%8E%9F%E7%90%86%E5%9B%BE%20%E4%B8%9D%E5%8D%B0%E5%9B%BE%20%E5%B0%BA%E5%AF%B8%E5%9B%BE%20%E4%BD%8D%E5%8F%B7%E5%9B%BE/%E6%A0%B8%E5%BF%83%E6%9D%BF/V1.0/LS2K0300_CoreBoard%20V1.0%20%E5%8E%9F%E7%90%86%E5%9B%BE.pdf)制作

将USB口朝上时：

- 左侧

| 引脚号(逐飞给的原理图封装) | 丝印 | 芯片引脚 | GPIO复用 | 主功能复用 | 第一复用 | 第二复用 | 引脚号(逐飞给的原理图封装) | 丝印 | 芯片引脚 | GPIO复用 | 主功能复用 | 第一复用 | 第二复用 | 备注 |
| :----------------------: | :-: | :------: | :-----: | :--------: | :-----: | :-------: | :----------------------: | :-: | :------: | :-----: | :--------: | :-----: | :-------: | :-: |
| 2                        | GND | GND      | -       | GND        | -       | -         | 1                        | GND | GND      | -       | GND        | -       | -         | 地 |
| 4                        | 5V  | -        | -       | -          | -       | -         | 3                        | 5V  | -        | -       | -          | -       | -         | 5V电源，不走芯片 |
| 6                        | 3V3 | -        | -       | -          | -       | -         | 5                        | 3V3 | -        | -       | -          | -       | -         | 3V3电源，经过一些处理后进入芯片，不直通芯片 |
| 8                        | VRTC | -       | -       | -          | -       | -         | 7                        | CR  | -        | -       | -          | -       | -         | 左为RTC电源，右和系统指示灯(你板子上那个SYSRDY)连一起 |
| 10                       | A1  | ADC_IN1  | -       | -          | -       | -         | 9                        | A0  | ADC_IN0  | -       | -          | -       | -         | 小心使用，高电压灌进去必烧，最好小于1.8V |
| 12                       | A3  | ADC_IN3  | -       | -          | -       | -         | 11                       | A2  | ADC_IN2  | -       | -          | -       | -         | - |
| 14                       | A5  | ADC_IN5  | -       | -          | -       | -         | 13                       | A4  | ADC_IN4  | -       | -          | -       | -         | - |
| 16                       | A7  | ADC_IN7  | -       | -          | -       | -         | 15                       | A6  | ADC_IN6  | -       | -          | -       | -         | - |
| 18                       | P28 |GMAC0_RX_CTL| GPIO28|gmac0_rx_ctl| -       | tim1_ch1  | 17                       | G0RC|GMAC0_RXCK| -       | -          | -       | -         |逐飞派并不使用GMAC0/GMAC1，而走的WIFI模块接UART3，所以部分GMAC引脚被复用出去|
| 20                       | P30 | GMAC0_RX1| GPIO30  |gmac0_rx[1] | -       | tim1_ch3  | 19                       | P29 | GMAC0_RX0| GPIO29  |gmac0_rx[0] | -       | tim1_ch2  | - |
| 22                       | P32 | GMAC0_RX3| GPIO32  |gmac0_rx[3] | -       | tim1_ch2n | 21                       | P31 | GMAC0_RX2| GPIO31  |gmac0_rx[2] | -       | tim1_ch1n | - |
| 24                       |G0TCO|GMAC0_TXCK_O| -     | -          | -       | -         | 23                       |G0TCI|GMAC0_TXCK_I| -     | -          | -       | -         | 我正在思考：为什么逐飞会把这堆用不了的引脚引出来 |
| 26                       | P34 | GMAC0_TX0| GPIO34  |gmac0_tx[0] | -       | tim2_ch1  | 25                       | P33 |GMAC0_TX_CTL| GPIO33|gmac0_tx_ctl| -       | tim1_ch3n | - |
| 28                       | P36 | GMAC0_TX2| GPIO36  |gmac0_tx[2] |can_rx[0]| tim2_ch3  | 27                       | P35 | GMAC0_TX1| GPIO35  |gmac0_tx[1] | -       | tim2_ch2  | - |
|30|P38|GMAC0_MDCK|GPIO38|gmac0_mdck|can_rx[1]|-|29|P37|GMAC0_TX3|GPIO37|gmac0_tx[3]|can_tx[0]|-|-|
|32|G1RC|GMAC1_RXCK|-|-|-|-|31|P39|GMAC0_MDIO|GPIO39|gmac0_mdio|can_tx[1]|-|-|
|34|G1TCO|GMAX1_TXCK_O|-|-|-|-|33|G1TCI|GMAX1_TXCK_I|-|-|-|-|-|
|36|P49|I2C0_SDA|GPIO49|i2c_sda[0]|gmac1_tx_ctl|lio_data[9]|35|P48|I2C0_SCL|GPIO48|i2c_scl[0]|gmac1_rx[3]|lio_data[8]|-|
|38|P51|I2C1_SDA|GPIO51|i2c_sda[1]|gmac1_tx[1]|lio_data[11]|37|P50|I2C1_SCL|GPIO50|i2c_scl[1]|gmac1_tx[0]|lio_data[10]|-|
|40|P53|I2C2_SDA|GPIO53|i2c_sda[2]|gmac1_tx[3]|lio_data[13]|39|P52|I2C2_SCL|GPIO52|i2c_scl[2]|gmac1_tx[2]|lio_data[12]|-|
