# Design and Interfacing of Serial Peripheral Interface (SPI) with SRAM Array in 0.6um CMOS

## Abstract
This project report provides details on the semi-custom design of SPI Interface with SRAM Array for IOT based embedded system implemented in a 0.6μm CMOS technology. The SPI Interface which aids in the write and read operations from a (16 x 16) bit SRAM was designed, simulated, layout done and tested successfully using Cadence and Spectre. The innovation of this project lies in creating and controlling all the signals required for the SRAM without use of internal clocks, deriving all control signals from the SPI signals themselves instead, thereby making it a simple and scalable circuit that can be made to consume very little power with slower access time.

## Introduction
Serial Peripheral Interface or SPI is a synchronous serial communication protocol that provides full – duplex communication at very high speeds. It is a master – slave type protocol that provides a simple and low-cost interface between a microcontroller and its peripherals. It has a single master and can have one or multiple slaves.   

A common serial port is called ‘asynchronous’ because the data sent and received are not synced with each other hence leading to some discrepancies. Therefore, asynchronous serial connections add extra start and stop bits to each byte as well as the transmission speed is set to help the receiver sync up to data as it arrives. These extra bits require lot of overhead and also contribute to complex hardware. On the other hand, SPI is a ‘synchronous’ data bus which uses separate lines for data and a clock that helps for perfect sync between both sides.  

SPI is called a four-wire serial bus consisting of four signals/pins: -
 - MOSI(Master Out Slave In) - Data flows from master to slave through it.
 - MISO(Master In Slave Out) - Data flows from slave to master through it.
 - SCLK(Synchronous Clock) - Generated from the master to make clock synchronous with data signals of the slave.
 - CS/SS(Chip Select/Slave Select) – Signal to select a particular slave used by master for communication.  
 
The master controls the clock frequency, polarity and phase w.r.t. data. The CPOL bit sets the polarity of the clock signal during the idle state. The CPHA bit selects the clock phase. Depending on the CPHA bit, the rising or falling clock edge is used to sample and/or shift the data. A master-slave pair must use the same set of parameters: SCLK frequency, CPOL, and CPHA for an effective communication. Depending on the CPOL and CPHA bit selection, four SPI modes are available as shown in Table I. Out of the four modes, mode 3 is implemented in this project. 

|  SPI Modes |	CPOL | CPHA | Idle Clock  |	Data Rx/Tx from Master        |
|:------------------:|:---------------:|:---------------:|:---------------:|:---------------:|
| 0  | 0  | 0  | Low | Rising Edge Sample, Falling Edge Data | 
| 1  | 0  | 1  | Low | Falling Edge Sample, Rising Edge Data |
| 2  | 1  | 1  | High | Falling Edge Sample, Rising Edge Data |
| 3  | 1  | 0  | High | Rising Edge Sample, Falling Edge Data |

Table 1: SPI Modes






