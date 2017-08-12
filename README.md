# attiny24a_spi
attiny24a SPI and ADC implementation

# Banana PI as programmer (M1)

Instruction for bananian. You should use `bpi` branch. It contains correct Makefile and `avrdude.conf`.

## WiringPi

First of all you will need support of GPIO. For that install WiringPI library:

    git clone https://github.com/BPI-SINOVOIP/BPI-WiringPi.git -b BPI_M1_M1Plus    
    cd BPI-WiringPi
    sudo chmod +x ./build
    sudo ./build
  
    # check that all is ok
    gpio readall
  
## Install required packages
  
    apt-get install gcc-avr avr-libc
  
    #for avrdude compilation
    sudo apt-get install -y build-essential bison flex automake libelf-dev libusb-1.0-0-dev libusb-dev libftdi-dev libftdi1
  
## Install avrdude with GPIO (you can download newer version)

    wget http://download.savannah.gnu.org/releases/avrdude/avrdude-6.1.tar.gz
    tar xvfz avrdude-6.1.tar.gz
    cd avrdude-6.1
    ./configure --enable-linuxgpio
    make
    sudo make install
  
## Connect your chip to SPI ports correctly.
  
  MISO, MOSI and SCLK like in image. Use CS0 for reset.

![image](https://i0.wp.com/hardware-libre.fr/wp-content/uploads/2014/07/gpio.png)

## Program the chip
  
    sudo make
