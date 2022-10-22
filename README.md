# ChirpStack Concentratord

![Tests](https://github.com/brocaar/chirpstack-concentratord/actions/workflows/main.yml/badge.svg?branch=master)

ChirpStack Concentratord is an open-source LoRa(WAN) concentrator daemon, part
of the [ChirpStack](https://www.chirpstack.io/) project. It exposes a [ZeroMQ](https://zeromq.org/)
based API that can be used by one or multiple applications to interact with
gateway hardware. By implementing and abstracting the the hardware specifics
in a separate daemon and exposing this over a ZeroMQ based API, the packet
forwarding application can be completely decoupled from the gateway hardware.
It also allows for running multiple packet forwarding applications simultaniously.

1.1 HAL介绍
这部分也就是LoRa集中器的HAL层(LoRa concentrator Hardware Abstraction Layer)，它是个C库，让大家使用少量的C函数就可以对LoRa集中器芯片进行配置硬件，以及收发数据包。

LoRa集中器是数字化的多信道多数据包标准的射频芯片，使用LoRa或者FSK模式进行收发数据。

1.2 HAL的组成
这个库是由6(8)个模块组成：

loragw_hal
主模块，包含高等级函数来配置和使用集中器

loragw_reg
这个模块用来操作集中器的寄存器

loragw_spi
通过SPI接口来操作集中器的寄存器

loragw_aux
包含一个主机需要的wait_ms函数，用于指定ms的延时

loragw_gps
通过基准时基来同步集中器内部计数，例如例程中的GPS授时。

loragw_radio
配置 SX125x 和 SX127x。

loragw_fpga (only for SX1301AP2 ref design)
SX1301AP2参考设计才需要，用于操作FPGA的寄存器，以及配置FPGA功能。

loragw_lbt (only for SX1301AP2 ref design)
SX1301AP2参考设计才需要，用于配置和使用LBT功能。


## Documentation

Please refer to the [ChirpStack documentation](https://www.chirpstack.io/) for
more information.

## License

ChirpStack Concentratord is distributed under the MIT license. See
[LICENSE](https://github.com/brocaar/chirpstack-concentratord/blob/master/LICENSE).
