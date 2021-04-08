# Installing qflow

 - Date created: 03-Apr-2021
 - Last updated: 07-Apr-2021

Just a record to remind myself of what I did to install qflow.

As done on an Ubuntu 18.04 system.

---

It's always better to read the README file first (though I'm sometimes too lazy for that and read it a bit too late). 

## Dependencies
qflow has the following dependencies that must be installed separately:

 - Yosys
 - graywolf
 - Qrouter
 - Magic
 - netgen
 - python3

The following are also qflow dependencies. But for me, installing the above dependencies had somehow caused these to be installed as well. Or may be it was just because it was already there on my computer.

 - tclsh
 - wish
 - tcsh

### Yosys
Does Verilog [RTL](https://en.wikipedia.org/wiki/Register-transfer_level) synthesis (Verilog parser/synthesis).

#### Installing from package:

    sudo apt install yosys

#### Compiling from source
Download the required file from [http://www.clifford.at/yosys/download.html](http://www.clifford.at/yosys/download.html).

I used v0.9

    tar -xf yosys-yosys-0.9.tar.gz
    cd yosys-yosys-0.9/
    make

Missing libraries need to be installed, if any. I needed:

    sudo apt install libreadline-dev flex

### graywolf
For placement in VLSI design (cell and pin placement).

#### Installing from package:

    sudo apt install graywolf

#### Compiling from source:
Go to [https://github.com/rubund/graywolf/releases](https://github.com/rubund/graywolf/releases) and download the files.

I used v0.1.6

    tar -xf graywolf-0.1.6.tar.gz
    cd graywolf-0.1.6
    mkdir build
    cd build
    cmake ..
    make
    sudo make install

Again, install missing libraries as needed.

I needed

    sudo apt install libgsl-dev  # GNU Scientific library

### Qrouter
Detail router.

#### Installing from package:

    sudo apt install qrouter

#### Compiling from source:
Download latest stable version from [http://opencircuitdesign.com/qrouter/download.html](http://opencircuitdesign.com/qrouter/download.html)

I used v1.4.84

    tar -xf qrouter-1.4.84.tgz
    cd qrouter-1.4.84/
    ./configure                 # Creates the Makefile
    make

In case of missing library errors, install them. I needed

    sudo apt install tk-dev tcl-dev

I also had to edit the Makefile to add flags for the compiler to find the tk header file. There are probably better ways to fix that but this one did work for me.

Edit `CFLAGS` variable from

    CFLAGS += -g -O2

to

    CFLAGS += -g -O2 -I /usr/include/tcl/

where `/usr/include/tcl/` is the path to the header file.

You can then install qrouter if you like with

    sudo make install

### Magic
Layout viewer.

    sudo apt install magic

### Netgen
Does [LVS](https://en.wikipedia.org/wiki/Layout_Versus_Schematic) (Layout-vs-Schematic) to verify whether the IC layout corresponds to the original schematic (circuit diagram) of the design.

Go to [http://opencircuitdesign.com/netgen/download.html](http://opencircuitdesign.com/netgen/download.html) and download the stable version.

I used v1.5

    tar -xf netgen-1.5.173.tgz
    cd netgen-1.5.173/
    ./configure
    make
    sudo make install

## qflow

Download the file from [http://opencircuitdesign.com/qflow/download.html#Download](http://opencircuitdesign.com/qflow/download.html#Download).

I got v1.4.95

    tar -xf qflow-1.4.95.tgz
    cd qflow-1.4.95/
    ./configure
    make
    sudo make install

### GUI

qflow GUI can be launched with

    qflow gui

I needed to copy the `tech/` directory from the extracted `qflow-1.4.95/` directory to `/usr/local/share/qflow` and install tkinter for python like

    sudo apt install python3-tk
    sudo cp -r tech/ /usr/local/share/qflow/

## References
 - [http://opencircuitdesign.com/qflow/download.html](http://opencircuitdesign.com/qflow/download.html)
 - [http://opencircuitdesign.com/qflow/install.html](http://opencircuitdesign.com/qflow/install.html)
 - [http://www.clifford.at/yosys/download.html](http://www.clifford.at/yosys/download.html)
 - [https://github.com/rubund/graywolf](https://github.com/rubund/graywolf)
 - [http://opencircuitdesign.com/qrouter/download.html](http://opencircuitdesign.com/qrouter/download.html)
 - [http://opencircuitdesign.com/magic/download.html](http://opencircuitdesign.com/magic/download.html)
 - [http://opencircuitdesign.com/netgen/](http://opencircuitdesign.com/netgen/)
 - [https://en.wikipedia.org/wiki/Layout\_Versus\_Schematic](https://en.wikipedia.org/wiki/Layout_Versus_Schematic)
 - [https://en.wikipedia.org/wiki/Register-transfer\_level](https://en.wikipedia.org/wiki/Register-transfer_level)
