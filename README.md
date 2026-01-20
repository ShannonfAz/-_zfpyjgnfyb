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

- 底下，从左到右看

| 引脚号(逐飞给的原理图封装) | 丝印 | 芯片引脚 | GPIO复用 | 主功能复用 | 第一复用 | 第二复用 | 引脚号(逐飞给的原理图封装) | 丝印 | 芯片引脚 | GPIO复用 | 主功能复用 | 第一复用 | 第二复用 | 备注 |
| :----------------------: | :-: | :------: | :-----: | :--------: | :-----: | :-------: | :----------------------: | :-: | :------: | :-----: | :--------: | :-----: | :-------: | :-: |
|42|P55|I2C3_SDA|GPIO55|i2c_sda[3]|gmac1_mdio|lio_data[15]|41|P54|I2C3_SCL|GPIO54|i2c3_scl[3]|gmac1_mdck|lio_data[14]|-|
|44|P41|UART0_TX|GPIO41|uart0_tx|gmac0_ptp_pps|lio_data[1]|43|P40|UART0_RX|GPIO40|uart0_rx|gmac0_ptp_trig|lio_data[0]|-|
|46|P43|UART1_TX|GPIO43|uart1_tx|gmac1_ptp_pps|lio_data[3]|45|P42|UART1_RX|GPIO42|uart1_rx|gmac1_ptp_trig|lio_data[2]|-|
|48|P45|UART2_RX|GPIO45|uart2_rx|gmac1_rx[0]|lio_data[5]|47|P44|UART2_TX|GPIO44|uart2_tx|gmac1_rx_ctl|lio_data[4]|注意这里开始和上面是反过来的|
|50|P47|UART3_RX|GPIO47|uart3_rx|gmac1_rx[2]|lio_data[7]|49|P46|UART3_TX|GPIO46|uart3_tx|gmac1_rx[1]|lio_data[6]|UART3为蓝牙串口|
|52|P69|CAN0_TX|GPIO69|can_tx[0]|spi0_cs[2]|uart1_dtr|51|P68|CAN0_RX|GPIO68|can_rx[0]|spi0_cs[1]|uart1_dsr|-|
|54|P71|CAN1_TX|GPIO71|can_tx[1]|-|uart1_ri|53|P70|CAN1_RX|GPIO70|can_rx[1]|spi0_cs[3]|uart1_dcd|P71为wifi使能脚，别动。|
|56|P73|CAN2_TX|GPIO73|can_tx[2]|sdio1_d[5]|gmac0_crs|55|P72|CAN2_RX|GPIO72|can_rx[2]|sdio1_d[4]|gmac0_col|-|
|58|P75|CAN3_TX|GPIO75|can_tx[3]|sdio1_d[7]|gmac1_crs|57|P74|CAN3_RX|GPIO74|can_rx[3]|sdio1_d[6]|gmac1_col|-|
|60|P82|TIM1_CH2|GPIO82|tim1_ch2|spi3_clk| i2c_scl[2]|59|P81|TIM1_CH1|GPIO81|tim1_ch1|-|-|-|
|62|P84|TIM1_CH1N|GPIO84|tim1_ch1n|spi3_mosi|i2c_scl[3]|61|P83|TIM1_CH3|GPIO83|tim1_ch3|spi3_miso|i2c_sda[2]|-|
|64|P86|TIM1_CH3N|GPIO86|tim1_ch3n|sdio1_d[4]|pwm[0]|63|P85|TIM1_CH2N|GPIO85|tim1_ch2n|spi3_cs|i2c_sda[3]|-|
|66|P88|TIM2_CH2|GPIO88|tim2_ch2|sdio1_d[6]|pwm[2]|65|P87|TIM2_CH1|GPIO87|tim2_ch1|sdio1_d[5]|pwm[1]|-|
|68|P76|I2S_MCLK|GPIO76|i2s_mclk|tim1_ch4|-|67|P75|CAN3_TX|GPIO75|can_tx[3]|sdio1_d[7]|gmac1_crs|-|
